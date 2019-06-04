# Java 修饰词
### 1.volatile 介绍
volatile 是 java 最轻量级的同步机制。

**特性：**
- 可见性。变量读写直接操作主存而不是 CPU Cache。当一个线程修改了 volatile 修饰的变量后，无论是否加锁，其它线程都可以立即看到最新的修改。
- 禁止指令重排序优化。
- 保证变量可见性，但无法保证原子性。即非线程安全。

**Java 内存模型：**
![image](img/16.png)
### 2.synchronized 介绍
线程安全，锁区域内容一次只允许一个线程执行，通过锁机制控制。
    
    一、当两个并发线程访问同一个对象 object 中的这个 synchronized(this) 同步代码块时，一个时间内只能有一个线程得到执行。
    另一个线程必须等待当前线程执行完这个代码块以后才能执行该代码块。

    二、然而，当一个线程访问 object 的一个 synchronized(this) 同步代码块时，另一个线程仍然可以访问该 object 中的
    非 synchronized(this) 同步代码块。

    三、尤其关键的是，当一个线程访问 object 的一个 synchronized(this) 同步代码块时，其他线程对 object 中所有其它
    synchronized(this) 同步代码块的访问将被阻塞。
- 同步块
```
public synchronized void method(int i);
```
每个类实例对应一把锁，类的两个实例没有这个限制。类实例中所有的 synchronized 方法共用这一把锁，锁的范围有点大。
