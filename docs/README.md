﻿# Castle Windsor 中文文档

<img align="right" src="images/windsor-logo.png">

Castle Windsor 是最好最成熟的 [IoC容器](ioc.md) ，可用于 .NET 和 Silverlight。

当前版本是 3.3.0， 发布于 2014 年 1 月。

* 查看 [发布记录](https://github.com/castleproject/Windsor/releases/tag/v3.3)
* [下载](https://github.com/castleproject/Windsor/releases/tag/v3.3)
* 获取官方编译版本 [NuGet](http://nuget.org/packages/Castle.Windsor): `PM> Install-Package Castle.Windsor`
* 或者 [获取预发布包](https://github.com/castleproject/Home/blob/master/prerelease-packages.md)

## 现成的代码

Windsor 的使用非常简单。 下面的代码不仅仅用于 *hello world* - 也是许多真实的大型项目使用 Windsor 的方式。  关于 API，功能，模式，和实践 的详细信息，查看完整文档。

```csharp
// 程序开始...
var container = new WindsorContainer();

// 使用WindsorInstallers为执行的程序集添加并配置所有组件
container.Install(FromAssembly.This());

// 实例化和配置根组件和它的依赖以及依赖的依赖...
var king = container.Resolve<IKing>();
king.RuleTheCastle();

// 清理，程序退出
container.Dispose();
```

那些 [安装器（installers）](installers.md) 是什么？ 这里有一个。

```csharp
public class RepositoriesInstaller : IWindsorInstaller
{
	public void Install(IWindsorContainer container, IConfigurationStore store)
	{
		container.Register(Classes.FromThisAssembly()
			                .Where(Component.IsInSameNamespaceAs<King>())
			                .WithService.DefaultInterfaces()
			                .LifestyleTransient());
	}
}
```
更多深入的例子可以尝试下面的内容，或者去钻研API文档。

## 示例和教程

通过完成一步一步的教程例子学习Windsor。

* [基础教程](basic-tutorial.md)
* [简单 ASP.NET MVC 3 应用 （To be seen）](mvc-tutorial-intro.md) - 从无到有一步一步开始。 此教程帮助你快速学习 Windsor 并对容器 API 的使用和如何最有效利用容器的模式有一定了解。

## 文档

* [Windsor 3.2 更新内容](whats-new-3.2.md)
* [Windsor 3.1 更新内容](whats-new-3.1.md)

### 概念

* [IoC 和 IoC 容器](ioc.md)
* [服务，组件和依赖](services-and-components.md)
* [组件是如何创建的](how-components-are-created.md)
* [依赖是如何解析的](how-dependencies-are-resolved.md)

### 使用容器

* [使用容器 - 如何使用、在哪里使用](three-calls-pattern.md)
* [Windsor 安装器 - 怎样把你的组件告诉 Windsor](installers.md)
* [注册 API 引用](fluent-registration-api.md)
* [使用 XML 配置](xml-registration-reference.md)
* [给容器传递参数](passing-arguments.md)
* [AOP，代理，和拦截器](interceptors.md)
* [调试和诊断支持](debugger-views.md)
* [性能计数器支持](performance-counters.md)

### 自定义容器

* [扩展点概述](extension-points.md)
* [生命期类型](lifestyles.md)
* [生命周期](lifecycle.md)
* [释放策略](release-policy.md)
* [组建模型构造支持器](componentmodel-construction-contributors.md)

### 扩展容器

* [设施](facilities.md)

### 知道另一个容器

* [Autofac 用户](windsor-for-autofac-users.md)
* [StructureMap 用户](windsor-for-structuremap-users.md)

## 资源

* [外部资源](external-resources.md) - screencasts, podcasts, etc
* [FAQ](faq.md)
* [路线图](roadmap.md)
