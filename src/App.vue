<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/> -->

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
 const { Gitlab } = require('gitlab');

@Component({
  name: 'App'
})
export default class App extends Vue {
  mounted() {
   const api = new Gitlab({
    token: "ACCESS_TOKEN" // Can be created in your profile.
  });
  api.Projects.all({ maxPages: 1, perPage: 40 }).then((data: any) => {
    console.log(data);
  }); 
  }
}
</script>


<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
