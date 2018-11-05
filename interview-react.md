#### react 生命周期
+ http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/
+ react 生命周期包括 初始化阶段，运行阶段 和销毁阶段
+ 初始化阶段：defaultProps, state，componentWiliiMount,render,componentDidMount
+ 运行阶段:componentWillreceiveProps,shuoldcomponentUpdate,componentwillUpdate,render,componentDidUpdate
+ 销毁阶段：componentwillUnmount

16.X 以后 三个will生命周期会被废弃，改用UNSAFE_xxxwillxxx
17 以后废弃三个wil生命周期

取而代之的是 getDerivedStateFromProps


#### 异步获取数据建议在componentDidMount 中的原因
+ 不建议在constructor中，会阻碍组件的实例化,阻碍组件的渲染
+ componentDidMount指的是第一次插入dom完毕,无论在同步和异步模式下都仅会触发一次
+ 在16.3之前的react版本中，是同步渲染的, 在componentWillMount中接口调用,有可能不会触发界面渲染,而在componentDidMount中渲染一定会触发界面渲染
+ 在16.3之后react开始异步渲染,在异步渲染模式下,使用componentWillMount会被多次调用,并且存在内存泄漏等问题
+ 关于在componentWillMount比componentDidMount请求早,具体应该是componentWillMount会立即执行,执行完之后会立即进行render
+ 在componentDidMount 被调用后,componentWillUnmount 一定会随后被调用到, 所以我们在componentDidMount里面注册的事件订阅都可以在这里取消掉,
而componentWillMount被调用并不能保证componentWillUnmount一定随后被调用


#### setState 是异步的吗
在生命周期和合成事件里是异步的，在原生事件里和setTimeout里是同步的
https://zhuanlan.zhihu.com/p/39512941 

#### react中的key
