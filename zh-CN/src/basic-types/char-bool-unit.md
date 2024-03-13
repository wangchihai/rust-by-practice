# 字符、布尔、单元类型
> 在 Rust 中，语句（Statements）和表达式（Expressions）有一些关键的区别。
`
表达式（Expressions）：表达式是计算出某个值的代码片段。例如，5 + 6 是一个表达式，因为它计算出值 11。函数调用（如 println!("Hello, world!")）和宏调用也是表达式。块 {}，如果它们以表达式结尾，也是表达式。
语句（Statements）：语句是执行某些操作但不返回值的代码片段。例如，let x = 5; 是一个语句，因为它创建了一个变量 x，但没有返回值。
在 Rust 中，函数体是由一系列语句构成的。如果你想让函数返回一个值，你需要在函数体的最后放一个表达式，而不是语句。这个表达式的值就会成为
函数的返回值。注意，这个表达式后面不能有分号，因为在 Rust 中，分号会把表达式转变为语句，而语句不返回值。
`
`
println 会返回() 语句默认返回()
`
### 字符
1. 🌟
```rust,editable
// 修改2处 `assert_eq!` 让代码工作 字符都是占4位

use std::mem::size_of_val;
fn main() {
    let c1 = 'a';
    assert_eq!(size_of_val(&c1),4); 

    let c2 = '中';
    assert_eq!(size_of_val(&c2),4); 

    println!("Success!")
} 
```

2. 🌟
```rust,editable
// 修改一行让代码正常打印
fn main() {
    let c1 = "中";
    print_char(c1);
} 

fn print_char(c : &str) {
    println!("{}", c);
}
```

### 布尔
3. 🌟
```rust,editable

// 使成功打印
fn main() {
    let _f: bool = false;

    let t = false;
    if !t {
        println!("Success!")
    }
} 
```

4. 🌟
```rust,editable

fn main() {
    let f = false;
    let t = true && false;
    assert_eq!(t, f);

    println!("Success!")
}
```


### 单元类型
5. 🌟🌟
```rust,editable

// 让代码工作，但不要修改 `implicitly_ret_unit` !
// 解1
// fn main() {
//     let v1: () = ();

//     let v = (2, 3);
//     assert_eq!(v1, implicitly_ret_unit());

//     println!("Success!")
// }

// fn implicitly_ret_unit() {
//     println!("I will return a ()")
// }
// 解2
fn main() {
    let v1: () = ();

    let v = (2, 3);
    assert_eq!(v, implicitly_ret_unit());

    println!("Success!")
}

fn implicitly_ret_unit()->(i32,i32) {
    println!("I will return a ()");
    (2,3)
}

// 不要使用下面的函数，它只用于演示！
fn explicitly_ret_unit() -> () {
    println!("I will return a ()")
}
```

6. 🌟🌟 单元类型占用的内存大小是多少？
```rust,editable

// 让代码工作：修改 `assert!` 中的 `4` 
use std::mem::size_of_val;
fn main() {
     let unit: (i32,i32,i32) = (2,4,8);//12
    let bb:()=(1) //4
    let cc:()=(1,2) //8

    println!("Success!")
}
```

> 你可以在[这里](https://github.com/sunface/rust-by-practice/blob/master/solutions/basic-types/char-bool.md)找到答案(在 solutions 路径下) 
