<script lang="ts" setup>
import { computed } from "vue";
import { useI18n } from "vue-i18n";
import reportEN from "../assets/report-en.png";
import reportZH from "../assets/report-zh.png";
import reportVN from "../assets/report-vn.png";
import otcEN from "../assets/OTC-en.png";
import otcZH from "../assets/OTC-zh.png";
import otcVN from "../assets/OTC-vn.png";
const { t } = useI18n();
interface imgs {
  otc: string;
  report: string;
}
const setImg = computed((): imgs => {
  const locale = t("flow.img");
  // if (locale === "en") {
  //   return {
  //     otc: otcEN,
  //     report: reportEN,
  //   };
  // } else {
  //   return {
  //     otc: otcZH,
  //     report: reportZH,
  //   };
  // }
  if (locale === "en") {
    return {
      otc: otcEN,
      report: reportEN,
    };
  }
  if (locale === "vn") {
    return {
      otc: otcVN,
      report: reportVN,
    };
  } else {
    return {
      otc: otcZH,
      report: reportZH,
    };
  }
});
</script>

<template>
  <div class="blockMix bg">
    <div class="block" style="flex-grow: 1"></div>
    <div class="contain">
      <div class="left"><img :src="setImg.report" alt="report" /></div>
      <!-- <div class="right">
        <div class="bg">
          <img :src="setImg.otc" alt="OTC trading" />
        </div>
      </div> -->
    </div>
    <div class="block" style="flex-grow: 1"></div>
  </div>
</template>

<style lang="scss">
@import "../scss/global.scss";
.blockMix {
  overflow: hidden;
  background: #009393;
  display: flex;
  flex-direction: row;
  .contain {
    padding: 50px 10px;
    width: 1440px;
    max-width: 1440px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    .right,
    .left {
      display: flex;
      align-items: center;
      // margin: 30px;
      max-width: 100%;
      justify-content: center;
      margin: auto;
      img {
        width: 100%;
      }
    }
    .right {
    }
    @include pad {
      .contain {
        padding: 0;
        flex-direction: column;
        justify-content: center;
      }
      .right,
      .left {
        margin: 0;
        display: flex;
        align-items: center;
        margin: 30px;
        max-width: 100%;
        img {
          width: 100%;
        }
      }
      .right {
        img {
          max-width: 100%;
        }
      }
    }
    @include phone {
      .contain {
        padding: 0;
        flex-direction: column;
        justify-content: center;
      }
      .right,
      .left {
        margin: 0;
        display: flex;
        align-items: center;
        margin: 10px 5px;
        max-width: 100%;
        img {
          width: 100%;
        }
      }
      .right {
        img {
          max-width: 100%;
        }
      }
    }
  }
}
.bg {
  background-image: url("/src/assets/tether.png");
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center center;
  img {
    max-width: 100%;
  }
}
</style>
