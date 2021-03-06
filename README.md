
## 1. 依赖工具
Gradle
Git
JDK1.8+
IntelliJ IDEA

## 2. 源码拉取
  2.1、从官方仓库 https://github.com/spring-projects/spring-framework Fork 出属于自己的仓库。

  2.2、本文使用的 Spring 版本为 5.2.x，最新版的编译有问题，不知道是gradle版本的原因还是什么，用的Gradle 7.1.1版本；

## 3. 预编译 spring-oxm 项目
  打开 IDEA Terminal ，输入如下命令，预编译 spring-oxm 项目：
  `./gradlew :spring-oxm:compileTestJava`
  当看到 BUILD SUCCESSFUL ，说明编译成功。

## 4. 运行示例
  在 spring-context 项目中的 src/test/java/example 目录下，已经提供了一些示例。

  #### ① 解析 XML 配置文件成对应的 BeanDefinition 们的流程

  可调试 org.springframework.beans.factory.xml.XmlBeanDefinitionReaderTests 的 #withFreshInputStream() 和 #withImport() 这两个单元测试。

  相比来说，后者比前者多了一个 <import /> 标签的解析。当然，XmlBeanDefinitionReaderTests 类中，其它方法也可以简单调试下。

  factorySingleton() 方法，单例的 FactoryBean 的单元测试。

  #### ② 加载 Bean 的流程

  可调试 org.springframework.beans.factory.xml.AbstractBeanFactoryTests 这个单元测试类里的方法。

  实际上，AbstractBeanFactoryTests 是一个抽象类，所以在运行时，需要选择对应的子类，例如 XmlListableBeanFactoryTests 类。

  #### ③ ClassPathXmlApplicationContext 的流程

  可调试 org.springframework.context.support.ClassPathXmlApplicationContextTests 这个单元测试类里的方法。例如 #testResourceAndInputStream() 方法。

  #### ④ 解析 Properties 配置文件成对应的 BeanDefinition 们的流程

  可调试 org.springframework.beans.factory.support.PropertiesBeanDefinitionReaderTests 这个单元测试里的方法。

  另外，也推荐阅读下 [《spring beans源码解读之 – BeanDefinition 解析器》](https://www.bbsmax.com/A/KE5QLe8PJL/) 一文。

  #### ⑤ 调试 Spring AOP 相关的流程

  参见 [《精尽 Spring 源码分析 —— AOP 源码简单导读》](http://svip.iocoder.cn/Spring/aop-simple-intro)

  #### ⑥ 调试 Spring Transaction 相关的流程

  参见 [《精尽 Spring 源码分析 —— Transaction 源码简单导读》](http://svip.iocoder.cn/Spring/transaction-simple-intro)

  #### ⑦ 调试 Spring MVC 相关的流程

  参见 [《精尽 Spring MVC 源码分析 —— 调试环境搭建》](http://svip.iocoder.cn/Spring-MVC/build-debugging-environment)
