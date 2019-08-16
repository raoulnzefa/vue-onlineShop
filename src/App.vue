<template>
  <div id="app">
    <div id="nav" class="nav-wrapper">
      <router-link to="/" class="nav-left">
        <i class="fad fa-scarf"></i>
        <h3>Clothing4U</h3>
      </router-link>
      <div class="nav-right">
        <router-link to="/">Home</router-link>|
        <router-link :to="{name: 'gender-overview', params: {gender: 'women'}}" class>Womens</router-link>|
        <router-link :to="{name: 'gender-overview', params: {gender: 'men'}}" class>Mens</router-link>|
        <router-link to="/cart">
          Cart
          <CounterBadge :count="cartCount" />
        </router-link>
      </div>
    </div>
    <div class="hero" v-if="$route.path === '/'">
      <div class="hero-text">
        <h2>Fashion straight to your home</h2>
        <p>Shop online today</p>
      </div>
    </div>
    <router-view />
  </div>
</template>
<script>
import CounterBadge from "./components/CounterBadge.vue";
export default {
  name: "App",
  components: {
    CounterBadge
  },
  computed: {
    cartCount() {
      return this.$store.state.cart.length;
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}
.hero {
  background-image: url("../src/assets/img/hero2.jpg");
  background-position: top;
  background-size: cover;
  height: 60vh;
  width: 100vw;
}

.hero-text {
  padding-top: 5rem;
  padding-left: 4rem;
  color: lightgrey;
  h2 {
    font-size: 2rem;
    @media (max-width: 800px) {
      font-size: 1.7rem;
    }
  }
  p {
    font-size: 1.4rem;
    @media (max-width: 800px) {
      font-size: 1.1rem;
    }
  }
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
}
#nav {
  padding: 0.01rem 5rem;
  background-color: #464a53;
  // #827B78
  // background: linear-gradient(to bottom right, #464a53 50%, #827b78);
  background: black;
  position: sticky;
  top: 0;
  a {
    font-weight: bold;
    color: white;
    &.router-link-exact-active {
      color: lightgrey;
    }
  }
}

.nav-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
}

.nav-left {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  font-size: 24px;
  color: white;
  // width: 300px;
  i {
    font-size: 32px;
    padding-right: 10px;
  }
}
.nav-right {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  width: 300px;
  color: white;

  a {
    color: white;

    &:visited {
      color: white;
    }
  }

  router-link {
    color: white;
  }
}
ul {
  padding-left: 0;
  list-style: none;
  color: white;
}
</style>
