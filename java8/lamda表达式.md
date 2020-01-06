# Lamda表达式	

## Lamda	
lamda 是一个`匿名函数`,可以理解为一段可以传递的代码，使代码更简洁、更灵活；	

## 基础语法	
操作符：->	
操作符左侧：参数列表	
操作符右侧：需要执行的功能（lamda体）	

### 语法格式
+ 无参数、无返回值：Runable	
> （）-> System.out.Println("**") 

+ 一个参数，无返回值 ：Comsumer	
> （x）-> System.out.Println(x) 	
> 只有一个参数时，小括号可以省略：x ->  System.out.Println(x) 

+ 多个参数，lamda体多行语句：Comparator	
>
>```java
>Comparator<IntegerI> com = (x,y) -> {
>System.out.Println(x);
>return Integer.compare(x,y);
>}
>```
>大括号里只有一条语句，可省略
>

+ Lamda表达式参数列表的参数类型可以省略不写
JVM编译器可以通过上下文路径进行  “类型推断”  ；

## 函数式接口
Lamda表达式需要函数式接口的支持	
+ 函数式接口：接口中只有一个抽象方法的接口，称为函数式接口；	
+ @FunctionalInterface 注解，检验是否是函数式接口；

### 四大内置函数式接口
+ `Comsumer<T>` ：消费型接口；void accept(T , t)
+ `Supplier<T>`：供给型接口；T get( )
+ `Function<T,R>`：函数型接口；R apply(T , t)
+ `Predicate<T>`：断言型接口；boolean test(T , t)
+ 其他接口

## Lamda代替匿名内部类	
原匿名内部类:	
```java
public void test(){
        Comparator<Integer> com = new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return Integer.compare(o1,o2);
            }
        };
        TreeSet<Integer> tr = new TreeSet<>(com);
     }
```
改用lamda表达式：	
```java
public void test(){
        Comparator<Integer> com = (o1, o2) -> Integer.compare(o1,o2);
        TreeSet<Integer> tr = new TreeSet<>(com);
     }
```
> 局部内部类中定义一个同级别的局部变量，jdk1.7之前必须是 final，1.8之后可省略，默认就是；


