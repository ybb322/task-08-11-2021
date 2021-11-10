<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="12" md="12">
        <h1>tab-1</h1>
        <v-data-table
        :headers="headers"
        :items="apiData"
        :items-per-page="10"
        class="elevation-1"
    ></v-data-table>
    </v-col>
  </v-row>
</template>

<script>
import axios from 'axios'

export default {
    data () {
        return {
        headers: [
                {
                text: 'ID',
                value:'id'
                },
                {
                text: 'Name',
                value:'name'
                },
                {
                text: 'Username',
                value:'username'
                },
                {
                text: 'Email',
                value:'email'
                },
                {
                text: 'City',
                value:'address.city'
                },
                {
                text: 'Street',
                value:'address.street'
                },
                {
                text: 'Zipcode',
                value:'address.zipcode'
                },
                {
                text: 'Suite',
                value:'address.suite'
                },
                {
                text: 'Phone',
                value:'phone'
                },
        ],
        apiData: [],
        }
    },
    mounted() {
    const vm = this;
    axios
    .get('https://jsonplaceholder.typicode.com/users')
    .then(response => (this.apiData = response.data))
    .then(function (assign){
        console.log(vm.apiData)
    })
  },
  methods: {
    consoleLog () {
        console.log (this.apiData)
    }
  },
}
</script>