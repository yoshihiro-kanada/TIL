## app/javascript/packsについて
- webpacker環境でJavaScriptを開発する際には、app/javascript配下で作業をすることになる
- エントリーファイルとは、モジュールバンドラーでバンドルする際に、解析のスタート地点となるファイル。そのファイルの中でimportしているモジュールを順番にたどってバンドルを行う
-　app/javascript/packsの配下にエントリーファイルを置き、バンドルされたそれらのファイルをhtmlファイルから読み込む
- デフォルトでは、application.jsとhello_vue.jsが置かれている

## hello_vue.jsについて

```
import App from '../app.vue'
// 省略...
document.addEventListener('DOMContentLoaded', () => {
  const app = new Vue({
    render: h => h(App)
  }).$mount()
  document.body.appendChild(app.$el)
})
```
- 上記コードは、app/javascript/app.vueを読み込んでそれを画面に埋め込んでいる。
- エントリーファイルを読み込む処理をどこかに書かないといけない

## app/javascript/packs/hello.jsをhtml.erbで読み込むコード
```
<%= javascript_pack_tag 'hello.js' %>
```
- webpackerというgemを利用している
- javascript_pack_tagは'webpacker'gemが提供しているヘルパーメソッド

## Vue Routerとは
