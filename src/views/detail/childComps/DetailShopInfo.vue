<template>
  <div id="shop_info" v-if="Object.keys(shop).length != 0">
    <div class="shop_name">
      <img :src="shop.logo" alt="" />
      <span>{{ shop.name }}</span>
    </div>

    <div class="score_info">
      <div class="score_left">
        <div class="score_sell">
          <div>{{ sellValue }}万</div>
          <div style="font-size: 0.6rem;">总销量</div>
        </div>
        <div class="score_item">
          <div>{{ shop.goods }}</div>
          <div style="font-size: 0.6rem;">全部宝贝</div>
        </div>
      </div>
      <div class="score_right">
        <table>
          <tr v-for="(item, index) in shop.score" :key="index">
            <td>{{ item.name }}</td>
            <td :style="{ color: item.isBetter ? 'red' : 'green' }">
              {{ item.score }}
            </td>
            <td
              style="color: white;"
              :style="{ backgroundColor: item.isBetter ? 'red' : 'green' }"
            >
              {{ item.isBetter ? "高" : "低" }}
            </td>
          </tr>
        </table>
      </div>
    </div>
    <div class="come_shop">进店逛逛</div>
  </div>
</template>

<script>
export default {
  props: {
    shop: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  computed: {
    sellValue() {
      /* parseFloat(this.shop.sells / 10000).toFixed(1) */
      return Math.round((this.shop.sells / 10000) * 10) / 10;
    },
    betterScore(isBetter) {
      if (isBetter) {
        return "{ backgroundColor: red, color: white}";
      } else {
        return "{ backgroundColor: green, color: white}";
      }
    }
  }
};
</script>

<style scoped>

</style>
