<template>
  <div >
    
    
    <table style="width:100%">
      <thead>
        <th>Picture</th>
        <th>Name</th>
        <th>firstdID</th>
        <th>lastID</th>
        <th>openPrice </th>
        <th>volume</th>
        <th>bidPrice </th>
        <th>askPrice </th>
        <th>highPrice</th>
        <th>lowPrice</th>
        
      </thead>
      <tbody>
        <tr v-for="(value, index) in ProductData" :key="index">
          <td>{{ index+1}}</td>
          <td>{{ value.symbol }}</td>
          <td>{{ value.firstId }}</td>
          <td>{{ value.lastId }}</td>
          <td>{{ value.openPrice }}</td>
          <td>{{ value.volume }}</td>
          <td>{{ value.bidPrice }}</td>
          <td>{{ value.askPrice}}</td>
          <td>{{ value.highPrice }}</td>
          <td>{{ value.lowPrice }}</td>
        </tr>
      </tbody>
    </table>
    <button @click="loadProduct()">Load data</button>
  </div>
 
 
</template> 

<script setup>
import axios from "axios";
import { ref } from "vue";


const ProductData = ref([]);
const url = ref("https://data.binance.com/api/v3/ticker/24hr");

function loadProduct() {
  axios
    .get(url.value)
    .then((response) => {
      ProductData.value = response.data;
    })
    .catch((err) => {
      console.log(err);
    });
}
</script>

<style>
table , th , td {
  border: 1px solid white;
  text-align: center;
}

@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>

