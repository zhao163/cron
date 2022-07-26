# [demo](https://small-stone.github.io/vCrontab/dist/)

![](public/demo.png)

# vab-cron

vue 的 cron 组件，支持解析/反解析 cron 表达式，生成最近五次的符合条件时间，依赖 vue2 和 element-ui

## 安装方式

```
npm install vabCron
```

## 引入方式

```javascript
//全局引入
import vabCron from "vabCron";
Vue.use(vabCron); //使用方式：<vabCron></vabCron>

//单独引入
import vabCron from "vabCron";
export default {
  components: { vabCron },
};
```

## 代码示例

```javascript
<template>
    <div id="app">
        <div class="box">
            <el-input v-model="input" placeholder class="inp"></el-input>
            <el-button type="primary" @click="showDialog">生成 cron</el-button>
        </div>
        <el-dialog title="生成 cron" :visible.sync="showCron">
            <vabCron @hide="showCron=false" @fill="crontabFill" :expression="expression"></vabCron>
        </el-dialog>
    </div>
</template>

<script>
import vabCron from 'vabCron'
export default {
    components: { vabCron },
    data() {
        return {
            input: "",
            expression: "",
            showCron: false
        };
    },
    methods: {
        crontabFill(value) {
            //确定后回传的值
            this.input = value;
        },
        showDialog() {
            this.expression = this.input;//传入的 cron 表达式，可以反解析到 UI 上
            this.showCron = true;
        }
    }
};
</script>
```

## 参数

- expression
  传入的 cron 表达式，可以反解析到 UI 上

- hideComponent
  需要隐藏的组件数组，依次为`['second','min','hour','day','month','week','year']`

## 方法

- fill
  点击确定时，把选择好的值返回。

- hide
  关闭组件时的回调
