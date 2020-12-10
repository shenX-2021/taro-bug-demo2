##### 异步调用调用Taro.redirectTo不能正常跳转

在`app.jsx`的`componentDidMount`钩子里异步调用`Taro.redirectTo`方法会报错，同步调用则不会
```javascript
// app.jsx
class App extends Component {
    componentDidMount () {
        console.log('app mount')
        setTimeout(() => {
          Taro.redirectTo({url: '/pages/index/index'});
        });
    }
}
```

报错栈：
```shell script
index.esm.js?eb04:2680 showPage:fail Received a falsy component for route "/pages/index/index". Forget to export it?
```

```shell script
index.esm.js?eb04:2657 Uncaught (in promise) TypeError: Cannot read property 'componentDidShow' of undefined
    at Route.componentWillReceiveProps (index.esm.js?eb04:2657)
    at eval (index.esm.js?eb37:1900)
    at errorCatcher (index.esm.js?eb37:1749)
    at reRenderComponent (index.esm.js?eb37:1899)
    at ComponentWrapper.update (index.esm.js?eb37:2263)
    at patch (index.esm.js?eb37:993)
    at patchKeyedChildren (index.esm.js?eb37:1122)
    at patchArrayChildren (index.esm.js?eb37:1050)
    at patchChildren (index.esm.js?eb37:1064)
    at patch (index.esm.js?eb37:987)
```

<a href="https://github.com/gxsandzxl/taro-bug-demo2/blob/master/src/app.jsx">代码导航</a>
