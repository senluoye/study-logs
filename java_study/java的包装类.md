# java的包装类

## 引言

我在写HashMap的时候用到了一个写法：

```java
Map<int, int> maps = new HashMap<>();
```

上面这种写法是错误的，报错会提示意外的类型，并且需要一引用。

## 为什么需要包装类

 java并不是纯面向对象的语言，java语言是一个面向对象的语言，但是java中的基本数据类型却不是面向对象的，因为他们没有方法和属性，所以我们在实际使用中经常将基本数据类型转换成对象，让他们拥有方法和属性，便于操作，比如，集合的操作中，这时，我们就需要将基本类型数据转化成对象！

## 包装类和基本数据类型的关系

![](https://img2018.cnblogs.com/blog/1395687/201904/1395687-20190427100603451-1800197804.png)



### 装箱与拆箱

装箱就是基本数据类型转换为包类型，拆箱就是包装类型转换为基本数据类型。

~~~java
public class WrapperTestOne {
    public static void main(String[] args){
        //1.自动装箱
        int t1=1;
        Integer t2=t1;
        //2.手动装箱
        Integer t3=new Integer(t1);
        System.out.println("int类型t1="+t1);
        System.out.println("自动装箱，Integer类型对象t2="+t2);
        System.out.println("手动装箱，Integer类型t3="+t3);


        //1.自动拆箱
        int t4=t2;
        //2.手动拆箱
            //通过intValue()方法返回int值，还可以利用其他方法装换为其他类型
        int t5=t2.intValue();
        System.out.println("自动拆箱,int型t4="+t4);
        System.out.println("手动拆箱,int型t5="+t5);
    }

}
~~~

## 包装类的继承关系

![](https://img2018.cnblogs.com/blog/1504650/201901/1504650-20190122173636211-1359168032.png)



## 包装类的基本操作

![](https://img2018.cnblogs.com/blog/1504650/201905/1504650-20190511210543886-182915236.png)

可以看到，上面其实也包含着装箱拆箱的过程。
```java
public class TestInteger {
	public static void main(String[] args) {
        // TODO Auto-generated method stub
       Integer i1=new Integer(123);
       Integer i2 = new Integer("123");
       System.out.println("i1=i2:"+(i1==i2));//false
       System.out.println("i1.equals(i2):"+i1.equals(i2));
       System.out.println(i2);
       System.out.println(i2.toString());//说明重写了toString方法
       Integer i3=new Integer(128);
       System.out.println(i1.compareTo(i3));//-1
       System.out.println(i1.compareTo(i2));//0
       System.out.println(i3.compareTo(i2));//1
       //(1)Integer-->int    包装对象.intValue()
       int i=i1.intValue();
       System.out.println(Integer.max(10, 20));//返回最大值
       //(2)String -->int  包装类类名.parseInt(String s)
       int ii=Integer.parseInt("234");
       //(3)int -->Integer
       Integer i4=Integer.valueOf(123);
       //(4)int-->String
       String str=ii+"";
       String s=String .valueOf(ii);
       //(5)String-->Integer;
       Integer i5=new Integer("345");
       //(6)Integer-->String
       String ss=i5.toString();
       System.out.println(ss);
    }

}
```

下面是输出：

```java
i1=i2:false
i1.equals(i2):true
123
123
-1
0
1
20
345
```

