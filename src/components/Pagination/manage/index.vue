<template>
  <el-pagination
    layout="prev, pager, next"
    class="el_pagination"
    :pager-count="pagerCount"
    :page-count="totalPage"
    :current-page="currentPage"
    @current-change="(page)=>{currentPage=page}"
  ></el-pagination>
</template>
<script>
export default {
  data () {
    return {
      currentPage: 0
    }
  },
  watch: {
    currentPage: {
      deep: true,
      handler (currentPage) {
        this.$emit('input', currentPage)
      }
    }
  },
  props: {
    // 总页数
    totalPage: {
      type: Number,
      required: true
    },
    // 当前页码
    value: {
      type: Number,
      required: true
    },
    // 显示页码数
    pagerCount: {
      type: Number,
      default: () => 5
    }
  },
  mounted () {
    this.currentPage = this.value
  }
}
</script>
