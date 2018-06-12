<template>
    <ul>
      <li v-for="product in products" :key="product.id">
        {{ product.title }} - {{ product.price | currency }}
        <br />
        <button :disabled="!product.inventory" @click="addProductToCart(product)">
          Add To Cart
        </button>
      </li>
    </ul>
</template>

<style lang="css" scoped>
</style>

<script>
import { mapState, mapActions } from 'vuex'

export default {
  data () {
    return {
    }
  },
  computed: {
    ...mapState({
      products: state => state.products.all
    })
  },
  methods: {
    ...mapActions('cart', [
      'addProductToCart'
    ])
  },
  created () {
    this.$store.dispatch('products/getAllProducts')
  }
}
</script>
