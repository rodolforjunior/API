<template>
  <div class="container card">
    <i>"{{ dados }}"</i>
    <p>- Kanye West</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      dados: [],
      ler: "",
    };
  },
  methods: {
    getApi() {
      const self = this;
      axios({
        method: "get",
        url: "https://api.kanye.rest",
      }).then(function (response) {
        console.log(response);
        self.dados = response.data.quote;
      });
    },
  },
  created() {
    this.getApi();
  },
};
</script>

<style scoped>
.container {
  display: flex;
  text-align: center;
  font-size: 40px;
  margin: 0 auto;
  padding: 4%;
  border-radius: 8%;
}
</style>
