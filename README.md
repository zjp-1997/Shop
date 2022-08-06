# shop

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

node_moudles文件夹： 项目依赖文件夹

public文件夹： 一般放置一些静态资源（图片），需注意，放在public文件夹中的静态资源，webpack进行打包的时候会原封不动的打包到dist文件夹中

src文件夹： 程序员源代码文件夹
    assets文件夹： 一般也是放置静态资源（一般放置多个组件公用的静态资源），需注意，放置在assets文件夹里面静态资源，在webpack打包的时候，
    webpack会把静态资源当作一个模块，打包JS文件里

components文件夹：一般放置的是非路由文件（全局组件）

App.vue文件：唯一的根组件，Vue当中的组件

main.js：程序的入口文件，也是整个程序最先执行的文件

babel.config.js：配置文件（babel文件）

package.json：认为是项目的身份证，记录项目中的依赖，项目名称，项目如何运行

package-lock.json：缓存性文件


1、src文件夹简写方法，配置别名: @

jsconfig.json：

{
    "comilerOptions": {
        "baseUrl": "./",
        "paths": {
            "@/*": [
                "src/*"
            ]
        }
    },
    "exclude": [
        "node_moudles","dist"
    ]
}

2、路由分析

前端路由： key-value键值对

key： URL（地址栏中的路径）
value：相应的路由组件

注意：项目是上中下结构

路由组件： Home首页路由组件、Search路由组件、登录路由组件(Login)、注册路由（Register）
非路由组件：
Header、
Footer（在首页和搜索界面有）,但是在登录和注册页没有

3、完成非路由组件Header和Footer
    项目开发步骤： 
    1、书写静态页面（HTML+CSS）
    2、拆分组件
    3、获取服务器的数据动态展示
    4、完成相应的动态业务逻辑

    注意：创建组建的时候： 组件的结构 + 组件的样式 + 图片资源

4、路由组件的搭建
vue-router
components文件夹：经常放置非路由组件（共用全局组件）
pages文件夹：经常放置路由组件

5、配置路由：
    项目中的路由一般配置在router文件夹中
    步骤： 
    1、引入Vue
    2、引入Vue-Router
    3、使用Vue-Router，(vue.use(vue-router))
    4、配置路由：
        export default new VueRouter({
            route: [
                {
                    path: 
                    component: 
                }
            ]
        })
    5、用<router-view></router-view>标签使用路由

    路由跳转的两种形式：
    1、声明式导航： router-link，可以进行路由的跳转
    2、编程式导航： push | replace ，可以进行路由的跳转，声明式导航能做的，它都可以，此外还有一些其他功能

6、Footer路由的显示与隐藏
    Footer组件在Home、Search显示Footer
    Footer组件在Login、Register隐藏
    
    可以通过组件上的$rote.path去判断显示与隐藏Footer组件

7、路由传参 
    1、声明式导航： router-link，可以进行路由的跳转
    2、编程式导航： push | replace ，可以进行路由的跳转，声明式导航能做的，它都可以
    
    路由传参有两种方式：
    1、params: 属于路径当中的一部分，需要注意,在配置路由的时候需要占位
    2、query：不属于路径当中的一部分，需要注意,在配置路由的时候不需要占位，类似于ajax中的queryString / hoome?k=v&kv=

    // 第一种字符串形式
      // this.$router.push("/search/" + this.keyword + '?k=' + this.keyword);

      // 第二种：模板字符串
      // this.$router.push(`/search/${this.keyword}?k=${this.keyword.toUpperCase()}`)

      // 第三种写法： 对象写法,注意在router/index.js文件中给路由命名
      this.$router.push({
        name: 'search',
        params: {
          keyword: this.keyword
        },
        query: {
          k: this.keyword.toUpperCase()
        }
      })



8、Home模块拆分

    1）三级联动组件业务

9、axios二次封装
    为什么要进行二次封装？
    请求拦截器和响应拦截器
    请求拦截器：可以在发请求之前处理一些业务
    响应拦截器：当服务器返回数据以后，可以处理一些事情

10、统一接口管理

    项目小: 完全可以在组件的生命周期中

    项目大： 接口统一管理

11、跨域问题

    什么是跨域: 协议、域名、端口号不同请求，称之为跨域

    代理：json,CORE

12、进度条的使用（nprogress）
    // 引入进度条
    import nprogress from 'nprogress'
    //start: 进度条开始  done： 进度条结束

    // 引入进度条的样式
    import "nprogress/nprogress.css"

13、vuex状态管理
    vuex： 官方提供的一个插件，状态管理库，集中式管理项目中组件共用的数据。


14、完成typenav三级联动展示数据



15、函数的防抖与节流

节流： 在规定的时间间隔范围内不会重复出发回调，只有大于这个时间间隔才会触发回调，把频繁触发变为少量触发
     （用户操作很频繁，但是把频繁的操作变为少量操作）
防抖：前面的所有的触发都被取消，最后一次执行在规定的时间之后才触发，也就是说如果连续快速的触发，只会执行一次（用户操作很频繁，但是只执行一次）

三级联动节流操作（使用的频率较高）

16、三级联动组件的路由跳转与传递参数

    路由跳转： 声明式导航（router-link）、编程式导航（push || replace）

    三级联动： 如果使用声明式导航router-link，可以实现路由的跳转传参，但是会出现卡顿现象
            router-link：可以一个组件，当服务器返回数据以后，循环出很多的router-link组件【创建组件实例的】 1000+
            创建组件实例的时候，一瞬间创建1000+个内存，因此出现了卡顿现象。

    三级联动用户可以点击的： 一级分类、二级分类、三级分类，当用户点击时，Home模块跳转到Search模块，一级会把用户选中的产品（产品名字、ID）
                            在路由跳转的时候，进行传递


    编程式导航：采用自定义属性进行页面跳转传参



17、search模块：

    1）开发search中的TypeNav商品分类菜单（过度动画效果）

18、开发首页中的ListContainer组件和Floor组件

    接口返回的数据只有商品分类的数据,对于ListContainer组件和Floor组件的数据没有提供

    mock数据: 模拟数据,需要用到一个插件mockjs,mock数据不会和服务器进行任何通信
    mockjs使用的步骤:
    1)在src目录下创建一个mock文件夹,
    2)准备json数据(在mock文件夹中准备数据)
    3)把mock需要的图片放到public文件夹中,public文件夹在打包的时候,会原封不动的放到dist文件夹中
    4)开始mock虚拟数据,通过mockjs实现(创建mockServe.js实现模拟数据)
    5)mockServe.js文件在人口文件中引入

19、轮播图的引入
    
    1)安装Swiper插件: 最新版本6,安装5版本
      npm i swiper@5
    2)使用swiper
        1、引包(相应的css和js)
        2、调整页面结构
        3、创建swiper实例(new swiper)[轮播图添加动态展示效果]
    3)解决轮播图问题
      watch + nextTick: 数据监听，监听数据变化
      nextTick： 在下次DOM更新循环结束之后执行延迟回调，在  修改数据之后立即使用这个方法，获取更新后的DOM，
                可以保证页面中的结构一定是有的，经常和一些组件一起使用

20、开发floor组件

    1)组件之间通信方式
        (1)props: 实现父给子传值
        (2)自定义事件: $on  $emit 实现子给父传值
        (3)全局事件总线: $bus
        (4)消息订阅
        (5)插槽
        (6)vuex
    1)把首页当中的轮播图拆分为一个共用组件


21、Search模块开发


    1)排序
        1:综合排序  2:价格排序    升序: asc  降序: desc

        问题:
        order属性的属性值最多有多少种写法:
        1:asc
        2:desc
        2:asc
        1:desc

        应该考虑的问题:
        1)谁应该有类名: 通过order属性值当中是包含 1 还是 2,1代表综合,2代表价格
        2)谁应该有箭头: 谁有类名谁有箭头
        3)箭头用什么展示出来:
    
    2)分页功能开发
        1.分页展示需要的条件：
            1：页数(pageNo)
            2：每一页的数据(pageSize)
            3：总页数：(total)
            4: 连续的页面个数：(5 | 7)
        
        2.自定义分页器在开发的时候自己传递假数据，
        3.对于分页器而言，需要算出起始数字和结束数字
        4.分页器的动态展示：分为上中下三个部分（v-for可以遍历数字）

22、开发产品详情页面
    1) 静态组件(注册路由)
        1.当点击商品图片的时候跳转到对应的产品的详情页面，且需要把相应的产品ID传给详情页
    
    2) 发请求  API ---->  请求接口

    3) vuex  ----->  获取产品详细信息

    4) 动态展示组件

    1.加入购物车按钮
    路由跳转之前发起请求

    路由跳转成功并传递参数

    浏览器存储功能：本地存储（持久化）和会话存储（非持久化）,不能存储对象，需要转化为字符串

    购物车数量：要判断输入的数量不能是字符串和负数，并且不能为小数
    let value = e.target.value
      if(isNaN(value) || value < 1) {
        this.skuNum = 1
      } else {
        this.skuNum = parseInt(value)
      }
21、加入购物车功能

