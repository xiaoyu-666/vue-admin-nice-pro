<template>
  <img
    class="logo"
    alt="Vue logo"
    src="./assets/logo.png"
  >
  <HelloWorld :msg="msg" />
  <el-button
    type="danger"
    @click="handleClick"
  >按钮</el-button>
</template>

<script lang="ts">
import {defineComponent, reactive, toRefs} from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import {ElMessage} from 'element-plus'

interface State {
    msg: string
}

export default defineComponent({
    name: 'App',
    components: {
        HelloWorld
    },

    setup() {
        const state: State = reactive({
            msg: 'Welcome to Your Vue.js + TypeScript App'
        })
        const handleClick = e => {
            console.log(e)
            state.msg = '哈哈，我修改了这个数据啦，哈哈'
            ElMessage('只是一条消息提示')
        }
        return {
            handleClick,
            ...toRefs(state)
        }
    }
})
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
.logo {
    width: 50%;
}
</style>
