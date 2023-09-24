# traffic-master
星城货运系统

一: 项目流程

  主要阶段 	阶段组成              	里程碑 	交付成功         
  启动阶段 	1: 编制总体项目计划 2: 启动会	项目启动	总体项目计划/项目实施协议
  需求调研 	1: 需求采集 2: 需求确认   	需求结束	需求分析报告       
  软件实现 	写代码               	很多点 	软件功能确认表      
  装配数据 	数据部署              	    	             
  培训员工 	教会客户来使用系统         	    	             
  测试运行 	                  	    	测试报告 运行总结    
  验收   	项目的阶段验收 整体项目的验收   	验收完成	帮助文档         
  维护/运维	                  	    	运维记录         
  完成   	                  	    	             

通俗意义下面项目研发的几个阶段

1: 可行性分析

2: 需求分析

3: 概要设计

4: 详细设计

5: 编码

6: 测试阶段

7: 发版本

8 : 交付

二: 项目需求

1: 用户管理

2: 角色管理

3: 权限管理

4: 仓储功能

5: 运输功能

6: 包装整理

7: 流通归纳

8: 装卸搬运管理

9: 配送管理

10 : 信息服务功能

11: 财务管理

12: 申报管理

三: 项目研发

1: 数据库设计

2:前端页面模板

3: 项目整体框架的搭建

3.1 我们的每个业务模块是分开的

3.2 代码层次分离【完全的单体项目而言】

4： 业务功能开发

postman  基于JSON

四: 数据库建表

数据字典

五 : 项目规划

traffic-master 父工程

traffic-dependencies  依赖模块  作为我们所有项目的共用的父依赖模块

traffic-api   公共的接口 公共的实体类 异常 结果码

traffic-api-interface  通用的接口

traffic-api-entity    通用的实体类

traffic-api-execption 通用的异常

traffic-api-commons 通用的公共的组件

traffic-api-resultCode  通用的结果码

traffic-system  系统模块

traffic-customer 客户模块

traffic-storage 仓储模块

traffic-transport 运输模块

traffic-pack 包装模块

traffic-induce 流通模块

traffic-carry 搬运模块

traffic-delivery 交付模块

traffic-finance 财务模块

traffic-declare 申报模块

traffic-utils 通用的工具类

traffic-cache  缓存

traffic-mq 消息队列

traffic-search 搜索引擎

traffic-web 页面部分



六 : 项目通用的部分

1: 通用错误码规范 (10000 - 99999)

以后项目出现任何问题,只需要看到错误码就可以知道具体是哪个模块发生的问题

项目在扩大以后,错误码不够用 ;  特别注明   100000 (新添加的模块)

traffic-system  系统模块     10000 - 15555

用户管理		10000 - 10999

角色管理		11000 - 11999

权限管理		12000 - 12999

traffic-customer 客户模块  15556-19999

traffic-storage 仓储模块    20000-29999

traffic-transport 运输模块 30000-39999

traffic-pack 包装模块     40000-49999

traffic-induce 流通模块  50000 - 59999

traffic-carry 搬运模块      60000 - 69999

traffic-delivery 交付模块  70000 - 79999

traffic-finance 财务模块    80000 - 89999

traffic-declare 申报模块     90000 - 99999

traffic-utils 通用的工具类    1000 - 1999

traffic-cache  缓存                2000 - 2999

traffic-mq 消息队列			  3000 - 3999

traffic-search 搜索引擎		4000 - 4999

traffic-web 页面部分			 100-200

2: 日志配置

七 : 业务开发

1: 系统管理

a: 用户管理. CURD

增加用户   addUser

删除用户   delUser

修改用户   updUser

查询用户  selUser  selAllUser selUserByPage selUser

差一条,查所有,分页查,条件查

第一种  :  根据业务模块去区分 (Controller service repository)

第二种 : 根据不同的层次,所有的业务模块都是位于这个层次里面

2: 前后端分离项目的说明

API : 前端会给我们api数据; 后端响应api数据到前端

前端永远不要相信后台给的数据;

2.1 通过接口文档来进行约束和规范; 就是不能实时更新,更多的字段修改都是口口相传;



响应的基本格式

    {
       code: 0000,
       data:{
          msg:"success"
       }
    }
    {
       code: 0001,
       data:{
          msg:"add fail .",
          tip:"添加失败"
       }
    }
    
    {
       resultCode : 0000,
       resultMsg : "",
       result : {}
    }
    http :  200   40x    50x   

    {
       code : 000000,
       data : {
            msg : "".
            entity : {}
       }
    }
    //查询一条数据
    
    {
       code : 000000,
       data : {
            msg : "".
           total : 20,
           page : 2,
           pageSize : 3,
       
           list : [{},{},{}
           ]
       }
    }
    
    //分页查询数据
    
    {
       code : 000000,
       data : {
            msg : "".
            list : [
              {username : "jack","userpass" : "123"},{},{}
            ]
       }
    }
    //条件查询数据
    
    下拉框 : 复选框 : 单选框 ... checked : 0/1    enabel : 0/1

Swagger / SosoApi

rap

3: 系统管理的用户添加

i : 先走流程 把整个前端页面 -> 我们自己的接口(就是Controller) - >service -> Repository

ii: 真正的去开发;    参数校验 异常处理 日志记录 公共信息规范 前端实体类  后台数据库实体类

注释不低于 40% ;

4: 系统管理的用户删除

i: 单独删除一个

ii: 删除一个列表
