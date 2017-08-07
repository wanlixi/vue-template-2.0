# vue-template-2.0

# 2017-08-07 更新
vue-template-2.0
## 目录结构
![image](https://github.com/wanlixi/vue-template-2.0/blob/master/21502099809_.pic_hd.jpg)
### 1.新增加一个测试环境配置
(1)、
config/index.js
```
axios.defaults.baseURL = `https://github.com/wanlixi/${process.env.NODE_ENV}`
```
build/test.js
```
require('./check-versions')()

process.env.NODE_ENV = 'test'

var ora = require('ora')
var rm = require('rimraf')
var path = require('path')
var chalk = require('chalk')
var webpack = require('webpack')
var config = require('../config')
var webpackConfig = require('./webpack.test.conf')

var spinner = ora('building for test...')
spinner.start()

rm(path.join(config.test.assetsRoot, config.test.assetsSubDirectory), err => {
  if (err) throw err
  webpack(webpackConfig, function (err, stats) {
    spinner.stop()
    if (err) throw err
    process.stdout.write(stats.toString({
      colors: true,
      modules: false,
      children: false,
      chunks: false,
      chunkModules: false
    }) + '\n\n')

    console.log(chalk.cyan('  Build complete.\n'))
    console.log(chalk.yellow(
      '  Tip: built files are meant to be served over an HTTP server.\n' +
      '  Opening index.html over file:// won\'t work.\n'
    ))
  })
})
```
(2)、
(3)、
(4)、
(5)、
(6)、
(7)、

### 2.vuex配置附带说明
(1)、
```
<template>
  <div class="index">
    <ul>
      <li
        v-for="item in list">
        <p>{{item.email}}</p>  
        <p>{{item.color}}</p>  
      </li>
    </ul>
    <p>{{getFavoriteListLength}}</p>
    <button @click="ADD_FAVORITE">addFavorite</button>
  </div>
</template>

<script type="text/babel">
// import { mapActions , mapState, mapGetters, mapMutations } from 'vuex'
// import datePicker from 'vue-ios-datepicker'
import { mapState, mapActions, mapGetters } from 'vuex'
export default {
  data () {
    return {
      localList: [
        {email: 'aaa.aaa.aa', color: 'blue'}
      ]
    }  
  },
  computed: {
    ...mapState({
      // list: state => state.favoriteList,
      // list: 'favoriteList', // 等于 state => state.favoriteList,
      list (state) {
        return state.favoriteList.concat(this.localList)
      }
    }),
    ...mapGetters([
      'getFavoriteListLength'
    ]),
    // list () {
    //   return this.$store.state.favoriteList
    // }
  },
  mounted () {
  },
  methods: {
    ...mapActions([
      'ADD_FAVORITE' // 映射 this.ADD_FAVORITE() 到 this.$store.dispatch('ADD_FAVORITE')
    ]),
    // ...mapActions({
    //   addFavorite: 'ADD_FAVORITE' // 映射 this.addFavorite() to this.$store.dispatch('ADD_FAVORITE')
    // })
  }
}
</script>

<style lang="stylus" scoped>
</style>
```
(2)、
(3)、
(4)、
(5)、
(6)、
(7)、

