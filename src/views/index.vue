<template>
  <div id="index" ref="appRef">
    <div class="bg">
      <!--第一行-->
      <div class="d-flex jc-center">
        <span class="fs-xxxxxl">CF符文计算器网页版</span>
      </div>
      <!--第二行-->
      <div class="d-flex jc-between" style="margin-top: 20%;">
        <div style="width: 15%">
          <dv-border-box-1></dv-border-box-1>
        </div>
        <div style="width: 60%">
          <dv-border-box-8>
            <div class="d-flex flex-column jc-center ai-center px-2 py-2">
              <el-tag>武器伤害</el-tag>
              <el-input v-model="weaponHarm" placeholder="武器伤害" size="medium"
                        oninput="value=value.replace(/^\.+|[^\d.]/g,'')"></el-input>
              <el-tag>爆率</el-tag>
              <el-input v-model="weaponRate" placeholder="爆率" size="medium"></el-input>
              <el-tag>爆伤</el-tag>
              <el-input v-model="criticalHit" placeholder="爆伤" size="medium"></el-input>
            </div>
            <div class="d-flex jc-center">
              <el-tag type="warning" class="fs-xxxxl">最终伤害：{{getRate}}</el-tag>
            </div>
          </dv-border-box-8>
        </div>
        <div style="width: 15%">
          <dv-border-box-1></dv-border-box-1>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
  import drawMixin from "../utils/drawMixin";

  export default {
    name: "index",
    mixins: [drawMixin],
    data() {
      return {
        weaponHarm: 0,
        weaponRate: 0,
        criticalHit: 0,

      }
    },
    computed: {
      getRate() {
        const a = this.weaponHarm / 100
        const b = this.criticalHit / 100
        const c = this.weaponRate / 100 + 0.03
        const ans = (1 + a) * (1 + (1.5 + b) * c)
        return ans.toFixed(4)
      }
    },
    methods: {}
  }
</script>

<style lang="scss" scoped>
  @import '../assets/scss/index.scss';

  .Myinput {

  }
</style>
