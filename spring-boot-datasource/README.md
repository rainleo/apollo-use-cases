# Purpose

演示[Spring Boot Datasource](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-sql.html)如何通过Apollo配置中心实现动态数据切换数据源

# Instructions

1. 创建test1数据库，导入test1.sql
2. 创建test2数据库，导入test2.sql
3. 在Apollo配置中心创建AppId为`spring-boot-datasource`的项目
2. 在默认的`application`下做如下配置（按照实际的数据库连接信息填写）：

    ```properties
    spring.datasource.url = jdbc:mysql://127.0.0.1:3306/test1?autoReconnect=true&amp;useUnicode=true&amp;characterEncoding=utf-8
    spring.datasource.username = root
    spring.datasource.password = sasa
    ```
3. 运行`com.ctrip.framework.apollo.use.cases.spring.boot.datasource.Application`启动Demo
4. 程序启动后会持续打印kl
5. 在Apollo配置中心修改配置，把`spring.datasource.url`的值切换到`test2`并发布配置
6. 程序会持续打印ckl，说明动态切换数据源生效了
7. 更多信息可以参见博文：http://www.kailing.pub/article/index/arcid/198.html
