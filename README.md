# nuxt-project-init

> nuxt projectInit for axios + scss + px2rem + iview

## Usage

``` bash
# install dependencies
$ yarn # or npm install

# serve with hot reload at localhost:3000
$ yarn dev # or npm run dev

# build for production and launch server
$ yarn build # or npm run dev
$ yarn start # or npm run dev

# generate static project
$ yarn generate # or npm run generate
```
## Other

* eslint标准使用的是：vue/strongly-recommended，[规则见此](https://github.com/vuejs/eslint-plugin-vue#priority-a-essential-error-preventio)

* eslint其他一些个性化规则在eslintrc.js中查看备注

* 配置了webpack中resolve.alias的路径引用，可在utils文件夹中配置（非必须）

* 支持大小屏幕的适配，简单的支持移动端适配（拉伸等窄屏/默认以1280尺寸的设计图，更改见nuxt.config.js中postcss.remUnit）

* 简单的封装了axios的用法

```js
import request from 'service'
// get request
testRequest ({ commit }, payload) {
  let params = {

  }
  return new Promise((resolve, reject) => {
    (async () => {
      try {
        let data = await request.get(/* 地址 */ , params)
        commit({
          type: 'authInfo',
          data: data.data
        })
        resolve(data)
      } catch (error) {
        reject(error)
      }
    })()
  })
}
// post request
testRequest ({ commit }, payload) {
  let params = {
    username: 'yzy123456',
    password: '123456'
  }
  return new Promise((resolve, reject) => {
    (async () => {
      try {
        let data = await request.post(/* 地址 */ , params)
        commit({
          type: 'authInfo',
          data: data.data
        })
        resolve(data)
      } catch (error) {
        reject(error)
      }
    })()
  })
}
```
* document.title通过.vue文件中的
```js
head () {
  return {
    title: 'Hello World'
  }
}
```
* iview放弃按需引用（原因是作用不大，全局引用这样更加方便对这个库的使用），如需要按需引入，按照一下操作即可：

```js
yarn add babel-plugin-import -D // 安装babel-plugin-import

// .babelrc 根目录下新建babel文件
{
  "plugins": [["import", {
    "libraryName": "iview",
    "libraryDirectory": "src/components"
  }]]
}
// 引用
import { Button } from 'iview'
export default {
  components: {
    Button
  }
}
```
* 这里有一个坑：在使用iview中的clo标签时会报错，已经修改eslint语言检查，若使用vscode时候还需要在首选项----》设置---》"vetur.validation.template": false

* 后续发现问题会及时更新项目构建
