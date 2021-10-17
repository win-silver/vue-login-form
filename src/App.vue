<template>
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username"/>
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password"/>
    </div>
    <button type="submit">login</button>
  </form>
</template>

<script>
import axios from 'axios';

export default {
  data: function() {
    return {
      username: "",
      password: ""
    }
  },
  methods: {
    submitForm: async function() {
      const url = 'https://jsonplaceholder.typicode.com/users';
      const data = {
        username: this.username,
        password: this.password
      }
      try {
        const result = await axios.post(url, data);
        if(result.status === 201) alert("login!");
      } catch(error) {
        console.error(error);
      }
      
    }
  }
  
}
</script>

<style>

</style>