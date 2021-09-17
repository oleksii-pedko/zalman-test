<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-sm-3" v-for="hit of hits" :key="hit">
          <div class="card" style="width: 18rem;height: 400px!important;">
            <img v-bind:src="hit.largeImageURL" class="card-img-top" alt="..." style="min-height: 200px">
            <div class="card-body">
              <h5 class="card-title">{{ hit.tags }}</h5>
              <b class="btn btn-primary m-2">Likes: {{ hit.likes }}</b><b class="btn btn-outline-primary m-2">Commnets: {{ hit.likes }}</b>
            </div>
          </div>
          <h2></h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

// Import Bootstrap an BootstrapVue CSS files (order is important)
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name: 'App',
  data() {
    return {
      hits: []
    }
  },
  mounted() {
    axios.get('https://pixabay.com/api/?key=23430510-5f9a727293ecb6cd3e61aa9f0&q=cats&image_type=all&per_page=100')
        .then(response => {
          console.log(response);
          this.hits = response.data.hits;
        });
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
