<script setup>
import { ref,reactive,computed } from 'vue'
const message = ref('hello world')
const rawHtml = ref('<span style="color:red">陈清帅比</span>')
const flag = ref(true)
const refStr = ref('https://www.baidu.com')
const textStr = ref("默认信息")
const count = ref(1)
const originObj = {
  name:'qvtu',
  time:2025,
  class:'vue'
}
const movie = reactive({
  name:'哪吒',
  shouzhong:"很广",
  juqing:"有趣",
})
function movieFunction(){
  return movie.name=='哪吒'&&movie.juqing=="有趣"&&movie.shouzhong=="很广"
  ?"成功的"
  :"普通的"
}
const movieEvaluation = computed(()=>{
  return movie.name=='哪吒'&&movie.juqing=="有趣"&&movie.shouzhong=="很广"
  ?"成功的"
  :"普通的"
});
const originObjReactive = reactive(originObj)
console.log(originObj)
console.log(originObjReactive)
console.log(originObj === originObjReactive)
function display(){
  this.flag = !this.flag
}
const shuxue = ref(1)
const yinyu = ref(1)
const yuwen = ref(1)
const zongfen = computed(()=>{
  return (shuxue.value + yinyu.value + yuwen.value);
})
const pingjun = computed(()=>{
  return (shuxue.value+yinyu.value+yuwen.value)/3;
})
import { onBeforeMount,onMounted,onBeforeUpdate,onUpdated,onUnmounted } from 'vue'
onBeforeMount(() => {
  console.log("挂载前")
})
onMounted(() => {
  console.log('组件已挂载');
});
onBeforeUpdate(() => {
  console.log('更新前')
})
onUpdated(() => {
  console.log('组件已更新');
});

onUnmounted(() => {
  console.log('组件已卸载');
});
const studentInfoKeys = reactive({
  id:"学号",
  name:'姓名',
  live:'宿舍',
  scope:'成绩'
})
const bulidings = reactive(['一善书院','双馨书院','三创书院','四实书院','拾德书院'])
const studentInfos = reactive([
  { id:2005001,name:'张三',live:'一善书院',score:90},
  { id:2005001,name:'李四',live:'双馨书院',score:85},
  { id:2005001,name:'王五',live:'三创书院',score:60},
  { id:2005001,name:'周六',live:'四实书院',score:59},
  { id:2005001,name:'郑七',live:'拾德书院',score:15},
])
</script>

<template>
  <div>
    <h1>{{ message }}</h1>
    <p>直接插值：{{ rawHtml }}</p>
    <p>v-html解析：<span v-html="rawHtml"></span></p>
    <p v-show="flag">ccccsnbydmr</p><button @click="display()">切换显示</button>
    <p><a :href="refStr">百度官网</a></p>
    <div>
      <input type="textStr"  v-model="textStr">
      <p>双向数据绑定：{{ textStr }}</p>
    </div>
    <div>
      <button @click="count++">增加</button>
      <p>{{count}}</p>
      <button @click="count--">减少</button>
    </div>
    <div>
      电影《{{ movie.name }}》是:{{ movieEvaluation }}
    
      电影《{{ movie.name }}》是:{{ movieFunction() }}
    </div>
    <div>
      <!-- <p>查分</p>
      <p>英语:<input type="number" v-model="yinyu"></p>
      <p>数学:<input type="number" v-model="shuxue"></p>
      <p>语文:<input type="number" v-model="yuwen"></p>
      <p>总分：{{zongfen}}</p>
      <p>平均分:{{ pingjun }}</p> -->
      <table border="1">
  <thead >
    <tr>
      <th>学号(id)</th>
      <th>姓名(name)</th>
      <th>宿舍(live)</th>
      <th>成绩(score)</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(item,index) in studentInfos" :key="index">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.live }}</td>
      <td v-if="item.score>=60">及格</td>
      <td v-if="item.score<60">挂科</td>
    </tr>
  </tbody>
</table>
    
    </div>
  </div>
</template>

<style scoped>

</style>
