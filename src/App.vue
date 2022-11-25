<script setup>
import axios from 'axios';
import gql from "graphql-tag";


const url = "https://venia.magento.com/graphql";

const query = gql(`
{
  products(filter: {sku: {eq:""}}, pageSize: 5, currentPage: 3){
      items{
        name
        sku
        price_range{
          minimum_price{
            regular_price{
              value
              currency
            }
            final_price{
              value
              currency
            }
            discount{
                amount_off
                percent_off
            }
          }
          maximum_price{
            regular_price{
              value
              currency
            }
            final_price{
              value
              currency
            }
            discount{
              amount_off
              percent_off
            }
          }
        }
      }
    }
  }`)
  console.log("aaa");
  axios
      .post(url, {
        headers: {
          "Accept-Encoding": "gzip, deflate, br",
          "Content-Type": "application/json",
          "Accept": "application/json",
          "Connection": "keep-alive",
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Methods": "GET, POST, PATCH, PUT, DELETE, OPTIONS",
          "Access-Control-Allow-Headers": "Origin, Content-Type, X-Auth-Token"
        },
        query
      }).then((result) => {
  console.log(result.data)
});
</script>

<template>
  
</template>

<style scoped>

</style>
