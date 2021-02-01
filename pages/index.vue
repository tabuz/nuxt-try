<template>
  <v-container>
    <v-row>
      <v-col lg="12">
        <div>
          <h1>Nuxt Mountains</h1>
          <ul v-if="prices">
            <li v-for="(price, name) in prices" :key="name">{{name}} : {{price}}</li>
          </ul>
        </div>
      </v-col>
    </v-row>
  </v-container>
  
</template>

<script lang="ts">

import Vue from 'vue'
import {
  Component
} from 'nuxt-property-decorator'

import Binance from 'binance-api-node'


@Component
export default class Index extends Vue {
  message: string = 'Hello!';
  prices: Record<string, string> | null = null;
  
  async asyncData() {
    const crypto = Binance()
      let prices = await crypto.prices();
      console.log('Pirces fetching on server side');
      return { prices }
    }
}

</script>
