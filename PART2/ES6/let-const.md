# let 与 const、

## 2.1 let

从一个例子入手
ES5下

``` javascript
    var a = [];
    for(var i = 0; i < 10; i++) {
        a[i] = function() {
            console.log(i)
        }
    }
```

> 执行 a[6]()  //结果是10

ES6下

``` javascript
    var a = [];
    for(let i = 0; i < 10; i++) {
        a[i] = function() {
            console.log(i)
        }
    }
```

> 执行 a[6]()  //结果是6

如何在es5下实现相同的效果

``` javascript
    var a = [];
    function _loop(i) {
        a[i] = function() {
            console.log(i);
        }
    }

    for (var i=0; i<10; i++) {
        _loop(i)
    }

    //or
    var a = [];
    for(var i=0; i<10; i++) {
        (function loop(i){
            a[i] = funciton() {
                console.log(i);
            }
        })(i)
    }
```

- 不存在变量提升

   纠正了之前，在声明前值是undefind的问题。

  ``` javascript
        console.log(foo);  //输出undefined
        var foo = 1;
  ```

- 不允许重复声明
    let 不允许在相同作用域内重复声明统一变量。

- 暂时性死区
    在代码块内，使用let命令声明变量之前，改变量是不可用的。

- 只能在声明后使用

## 2.2 块级作用域

## 2.3 const

- 基本属性和let相同
- 声明一个只读的常量，一旦声明，常量的值就不能改变，改变就会报错啊

```javascript
     const PI = 3.1415;
     PI //3.1415

     PI = 2; //TypeError: Assignment to constant variable
```
