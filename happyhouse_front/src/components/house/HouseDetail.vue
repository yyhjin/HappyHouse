<template>
  <b-container v-if="house" class="bv-example-row">
    <b-row>
      <b-col
        ><br />
        <h2>{{ house.aptName }}</h2></b-col
      >
    </b-row>
    <b-row class="mb-2 mt-1">
      <!-- <b-col
        ><b-img :src="require('@/assets/apt.png')" fluid-grow></b-img
      ></b-col> -->
    </b-row>
    <b-row>
      <b-col>
        <b-alert show variant="secondary"
          >일련번호 : {{ house.aptCode }}</b-alert
        >
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-alert show variant="primary" style="color: #41464b"
          >아파트 이름 : {{ house.aptName }}
        </b-alert>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-alert show variant="info" style="color: #41464b"
          >법정동 : {{ house.dongName }}
        </b-alert>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-alert show variant="warning" style="color: #41464b"
          >건축 연도 : {{ house.buildYear }}년</b-alert
        >
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-alert show variant="danger" style="color: #41464b"
          >거래금액 :
          {{
            (parseInt(house.recentPrice.replace(",", "")) * 10000) | price
          }}원</b-alert
        >
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import { mapState, mapMutations } from "vuex";

const houseStore = "houseStore";

export default {
  name: "HouseDetail",
  computed: {
    ...mapState(houseStore, ["house"]),

    // house() {
    //   return this.$store.state.house;
    // },
  },
  filters: {
    price(value) {
      if (!value) return value;
      return value.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
  created() {
    // this.$store.dispatch("getSido");
    // this.sidoList();
    this.CLEAR_HOUSE_DETAIL();
    //this.getSido();
  },
  methods: {
    ...mapMutations(houseStore, ["CLEAR_HOUSE_DETAIL"]),
  },
};
</script>

<style></style>
