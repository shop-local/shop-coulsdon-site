<template>
  <div>
    <div class="block block-hero">
      <MenuButton/>

      <div class="block-sm-middle block-xs-bottom">
        <div class="container">
          <div class="row">
            <div class="col-lg-5">
              <h1 class="block-title mb-4">
                <img src="../assets/logo-white.png" class="text-ribbon text-ribbon-primary img-fluid" alt="Shop Coulsdon">
              </h1>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="block block-transparent block-angle block-map">
      <div class="block-bg-clip">
        <div class="block-bg">
          <LocalMap class="block-bg-img" id="home-map" v-bind:businesses="businesses" v-bind:carParks="carParks" />
        </div>
      </div>

      <div class="container">
        <div class="row justify-content-end">
          <div class="col-md-5 col-lg-4">
            <h1 class="block-title mb-4">
              <span class="text-ribbon text-ribbon-primary">
                <span class="text-serif">Shop Local</span>
              </span>
            </h1>

            <router-link to="/map" class="btn btn-square btn-primary btn-lg btn-block">Get exploring</router-link>
          </div>
        </div>
      </div>
    </div>

    <div class="block block-inverse block-businesses">
      <div>
        <div class="container">
          <div class="row mb-4">
            <div class="col-lg-6">
              <h1 class="block-title mb-4">
                <span class="text-ribbon">
                  <span class="text-serif">Shop Independant<br>Save Time &amp; Money</span>
                </span>
              </h1>
            </div>
          </div>

          <div class="row">
            <div class="col-lg-4" v-for="business in businesses.slice(0, 3)" v-bind:key="business.slug">
              <BusinessCard v-bind:business="business" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import MenuButton from '@/components/MenuButton.vue'
import BusinessCard from '@/components/BusinessCard.vue'
import LocalMap from '@/components/LocalMap.vue'
import businessesData from '@/assets/businesses.json'
import carParksData from '@/assets/car-parks.json'

export default {
  name: 'home',
  components: {
    MenuButton,
    BusinessCard,
    LocalMap
  },
  data () {
    return {
      businesses: businessesData,
      carParks: carParksData
    }
  }
}
</script>

<style scoped lang="scss">
@import "~@shop-local/shop-local-theme/scss/variables";

.block-hero {
  background-image: url(../assets/img/boxed-water-is-better-1464058-unsplash.jpg);

  .block-title {
    .text-ribbon {
      background-blend-mode: multiply;
      padding-top: 0;
      padding-bottom: 0;
    }
  }

  .row {
    margin-bottom: $spacer-y * 3;
  }
}

.block-grid {
  margin-top: $spacer-y;

  .container {
    position: relative;
    top: -($spacer-y * 3);
    z-index: 2;
  }

  img {
    width: 100%;
  }
}

.block-map {
  z-index: 3;
  margin-top: -($spacer-y * 2.5);
  margin-bottom: -($spacer-y * 2.5);

  .block-bg {
    border-top: ($border-width * 10) solid var(--primary);
    border-bottom: ($border-width * 10) solid var(--primary);
    right: -(max($spacer-x, $spacer-y) / 2);
    left: -(max($spacer-x, $spacer-y) / 2);
  }
}

.block-businesses {
  background-color: var(--secondary);
}
</style>
