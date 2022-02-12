# 本单元目标

## 一、为什么要学习数据库

1.持久化数据

2.方便检索

3.存储大量数据

4.共享、安全

5.通过组合分析，获取新的数据





## 二、数据库的相关概念      

​		**DBMS、DB、SQL**

DB:database数据库，存储一系列有组织数据的容器

DBMS：Database Management System数据库管理系统，使用DBMS管理和维护DB

SQL：StructureQueryLanguage结构化查询语言，程序员用于和DBMS通信的语言



## 三、数据库存储数据的特点

1、数据先放在表中，表再放在库中

2、一个库可以有多张表，每张表都有自己的唯一标识名

3、一张表的设计，类似于java中”类"的设计

​      表中的字段的设计，类似于属性的设计

​      表中的单条记录，类似于一个对象

​      表中的所有的记录，类似于对象的集合



​     orm ：object relation mapping 对象关系映射



## 四、初始MySQL

### 1、MySQL产品的介绍        

MySQL 前身属于瑞典的一家公司AB，2008年被sun公司收购，2009年sun被oracle公司收购。



特点：

① 体积小、安装较方便

②开源、免费

③性能高、稳定性好

④兼容性好



### 2、MySQL产品的安装          ★      

基于C/S架构的DBMS，需要安装服务端和客户端

www.oracle.com

MySQL5.5

###  

### 3、MySQL服务的启动和停止     ★

方式一：图形化

右击——计算机管理——服务——MySQL服务



方式二：通过管理员身份运行dos

net start 服务名

net stop 服务名





### 4、MySQL服务的登录和退出     ★    

###   

**方式一：通过dos命令**

mysql -h主机名 -P端口号 -u用户名 -p密码

**注意：**

如果是本机，则-h主机名  可以省略

如果端口号是3306，则-P端口号可以省略

**方式二：通过图形化界面客户端**

通过sqlyog，直接输入用户名、密码等连接进去即可





### 5、MySQL的常见命令和语法规范      

**①常见命令**

show databases             显示当前连接下所有数据库

show tables                    显示当前库中所有表

show tables from 库名  显示指定库中所有表

show  columns from 表名    显示指定表中所有列

use 库名                             打开/使用指定库



**②语法规范**

不区分大小写

每条命令结尾建议用分号

注释：

#单行注释

-- 单行注释

/*多行注释*/











## 五、DQL语言的学习   ★              

DQL:Data Query Language  数据查询语言

select



### 1、基础查询        ★          



语法：

select 查询列表 from 表名;

特点：

①查询结果集是一个虚拟表

②查询列表可以是单个字段、多个字段、常量、表达式、函数，可以是以上的组合

引申1：起别名

select 字段名  as  "别名" from 表名;

select 字段名 " 别名" from 表名;

引申2：+的作用

作用：加法运算

- 如果两个操作数都是数值型，则直接做加法运算

- 如果其中一个为非数值型，则将强值转换成数值型，如果转换失败，则当做0

'123'+4====》127

‘abc’+4====》 4

- 如果其中一个为null，则结果直接为null

引申3：去重

select distinct department_id from employees;

引申4：补充函数

select version();

select database();

select user();

select ifnull(字段名,表达式);

select concat(字符1，字符2,字符3);

select length(字符/字段);获取字节长度

### 

### 2、条件查询  	   ★



**语法：**

select 查询列表 

from 表名

where 筛选条件;



**特点：**

筛选条件的分类：

①按条件表达式筛选

关系运算符：>=   <   <=   >    <>   =

 

②按逻辑表达式筛选

逻辑运算符：and   or   not





③模糊查询

like:一般和通配符搭配使用

​     _ 任意单个字符

​    % 任意多个字符

between and：一般用于判断某字段是否在指定的区间

​		a between 10 and  100

in：一般用于判断某字段是否在指定的列表

​		a  in(10,30,50)



is null:判断null值

​	

### 3、排序查询  	   ★				

**语法：**

select  查询列表

from 表名

where 筛选条件

order by 排序列表 ;

**特点：**

①排序列表可以是 单个字段、多个字段、函数、表达式、别名、列的索引，以及以上的组合

②升序，通过asc

​    降序，通过desc

### 4、常见函数        ★               

说明：sql中的函数分为单行函数和分组函数

调用语法：select 函数名(实参列表);

1》字符函数

concat(str1,str2,..):拼接字符

substr(str,pos):截取从pos开始的所有字符，   起始索引从1开始

substr(str,pos,len):截取len个从pos开始的字符，起始索引从1开始

length(str):获取字节个数

char_length(str):获取字符个数

upper(str):变大写

lower(str):变小写

trim(【substr from】str):去前后指定字符，默认是去空格

left(str,len):从左边截取指定len个数的 字符

right(str,len):从右边截取指定len个数的 字符

lpad(str,substr,len):左填充

rpad(str,substr,len)：右填充

strcmp(str1,str2):比较两个字符的大小

instr(str,substr):获取substr在str中第一次出现的索引

2》数学函数

ceil(x):向上取整

floor(x):向下取整

round(x,d):四舍五入

mod(x,y):取模/取余

truncate(x,d):截断，保留小数点后d位

abs(x):求绝对值



3》日期函数

now():获取当前日期——时间

curtime():只有时间

curdate():只有日期

date_format(date,格式):格式日期为字符

str_to_date(str,格式):将字符转换成日期

datediff(date1,date2):获取两个日期之间的天数差

year(date)

month(date)

...



**4》流程控制函数**

①if(条件，表达式1，表达式2)：如果条件成立，返回表达式1，否则返回表达式2

②case 表达式

when 值1 then 结果1

when 值2 then 结果2

...

else 结果n

end

**③**

**case** 

when 条件1 then 结果1

when 条件2 then 结果2

...

else 结果n

end





### 5、分组函数        ★        

sum求和

avg平均

max最大

min最小

count个数



特点：

1》实参的字段的类型，sum和avg只支持数值型，其他三个可以支持任意类型

2》这五个函数都忽略null值

3》count可以支持以下参数

count(字段)：查询该字段非空值 的个数

count(*) ：查询结果集的行数

count(1)：查询结果集的行数

4》分组函数可以和distinct搭配使用，实现去重的统计

select count(distinct 字段) from 表;



###       

### 6、分组查询		   ★			

**语法：**

select 分组函数,分组的字段

from 表名

where 分组前的筛选条件

group by 分组列表

having 分组后的筛选条件

order by 排序列表;

**特点：**

1》分组列表可以是单个字段、多个字段

2》筛选条件分为两类

​				**筛选的基表		使用的关键字		位置**

分组前筛选	    原始表			where				group by前面



分组后筛选           分组后的结果集	having				group by后面



### 7、连接查询	 	★			

说明：当查询中涉及到了多个字段，则需要通过多表连接

笛卡尔乘积：

​	出现原因：没有有效的连接条件

​	解决办法：添加有效的连接条件

--------------------------SQL92语法------------------------

语法：

**select 查询列表**   ①

**from 表1 别名,表2 别名,... **②

**where 连接条件** ③

**and 筛选条件**④

group by 分组列表⑤

having 分组后筛选⑥

order by 排序列表;⑦



**执行顺序：**

②③④⑤⑥①⑦

--------------------------SQL99语法------------------------

**1》内连接**

语法：

select 查询列表    ①

from 表1 别名②

【inner】 join 表2 别名 on 连接条件  ③

【inner】 join 表3 别名 on 连接条件

where 筛选条件  ④

group by 分组列表⑤

having 分组后的筛选⑥

order by 排序列表⑦



**执行顺序：**

②③④⑤⑥①⑦





### 8、子查询       √          

一、含义
嵌套在其他语句内部的select语句称为子查询或内查询，
外面的语句可以是insert、update、delete、select等，一般select作为外面语句较多
外面如果为select语句，则此语句称为外查询或主查询

二、分类
1、按出现位置
select后面：
		仅仅支持标量子查询
from后面：
		表子查询
where或having后面：
		标量子查询
		列子查询
		行子查询
exists后面：
		标量子查询
		列子查询
		行子查询
		表子查询

2、按结果集的行列
标量子查询（单行子查询）：结果集为一行一列
列子查询（多行子查询）：结果集为多行一列
行子查询：结果集为多行多列
表子查询：结果集为多行多列

**三、示例**
where或having后面
1、单行子查询
案例：查询最低工资的员工姓名和工资
①最低工资
select min(salary) from employees

②查询员工的姓名和工资，要求工资=①
select last_name,salary
from employees
where salary=(
	select min(salary) from employees
);

**多行子查询**

2、列子查询
案例：查询所有是领导的员工姓名
①查询所有员工的 manager_id
select manager_id
from employees

②查询姓名，employee_id属于①列表的一个
select last_name
from employees
where employee_id in(
	select manager_id
	from employees
);        

### 9、分页查询       ★              

一、应用场景
当要查询的条目数太多，一页显示不全

二、语法

select 查询列表
from 表
limit 【offset，】size;
**特点**：
offset代表的是起始的条目索引，默认从0开始
size代表的是显示的条目数

②如果limit子句起始索引为0，则可以省略，limit 5等价为limit 0,5;

③公式：
假如要显示的页数为page，每一页条目数为size
select 查询列表
from 表
**limit (page-1)*size,size;**

### 10、union联合查询	√			



一、含义 union：合并、联合，将多次查询结果合并成一个结果

二、语法
查询语句1
union 【all】
查询语句2
union 【all】
...

三、意义
1、将一条比较复杂的查询语句拆分成多条语句
2、适用于查询多个表的时候，查询的列基本是一致



四、特点
1、要求多条查询语句的查询列数必须一致
2、要求多条查询语句的查询的各列类型、顺序最好一致
**3、union 去重，union all包含重复项**

## 六、DML语言的学习    ★             

### 1、插入语句	

一、方式一
语法：
insert into 表名(字段名,...) values(值,...);
特点：
1、要求值的类型和字段的类型要一致或兼容
2、字段的个数和顺序不一定与原始表中的字段个数和顺序一致
但必须保证值和字段一一对应
3、假如表中有可以为null的字段，注意可以通过以下两种方式插入null值
①字段和值都省略
②字段写上，值使用null
4、字段和值的个数必须一致
5、字段名可以省略，默认所有列

```mysql
INSERT INTO `user`(`id`,`name`,`pwd`) VALUES(1,'左1',123456),(2,'左2',12312312),(3,'左2',14234326)
```





二、方式二
语法：
insert into 表名 set 字段=值,字段=值,...;

两种方式 的区别：
1.方式一支持一次插入多行，语法如下：
insert into 表名【(字段名,..)】 values(值，..),(值，...),...;
2.方式一支持子查询，语法如下：
insert into 表名
查询语句;				

### 2、修改语句	

一、修改单表的记录 ★
语法：update 表名 set 字段=值,字段=值 【where 筛选条件】;

二、修改多表的记录【补充】
语法：
update 表1 别名 
left|right|inner join 表2 别名 
on 连接条件  
set 字段=值,字段=值 
【where 筛选条件】;					

### 3、删除语句	

方式一：使用delete
一、删除单表的记录★
语法：delete from 表名 【where 筛选条件】【limit 条目数】
二、级联删除[补充]
语法：
delete 别名1,别名2 from 表1 别名 
inner|left|right join 表2 别名 
on 连接条件
 【where 筛选条件】



方式二：使用truncate
语法：truncate table 表名

两种方式的区别【面试题】★

1. truncate删除后，如果再插入，标识列从1开始
     delete删除后，如果再插入，标识列从断点开始

2. delete可以添加筛选条件
    truncate不可以添加筛选条件

3. truncate效率较高

4. truncate没有返回值
   delete可以返回受影响的行数

5. truncate不可以回滚
   delete可以回滚					

## 七、DDL语言的学习  

### 1、库和表的管理	 √	

1>库的管理

一、创建库
create database 【if not exists】 库名【 character set 字符集名】;



二、修改库
alter database 库名 character set 字符集名;



三、删除库
drop database 【if exists】 库名;				

2》表的管理

一、创建表 ★
create table 【if not exists】 表名(
	字段名 字段类型 【约束】,
	字段名 字段类型 【约束】,
	。。。
	字段名 字段类型 【约束】 

)

```mysql
CREATE TABLE `user`(
   `id` INT NOT NULL PRIMARY KEY,
   `name` VARCHAR(30) DEFAULT NULL,
   `pwd` VARCHAR(30)
)ENGINE=INNODB DEFAULT CHARSET=utf8;
```



二、修改表

1.添加列
alter table 表名 add column 列名 类型 【first|after 字段名】;
2.修改列的类型或约束
alter table 表名 modify column 列名 新类型 【新约束】;
3.修改列名
alter table 表名 change column 旧列名 新列名 类型;
4 .删除列
alter table 表名 drop column 列名;
5.修改表名
alter table 表名 rename 【to】 新表名;

三、删除表
drop table【if exists】 表名;

四、复制表
1、复制表的结构
create table 表名 like 旧表;
2、复制表的结构+数据
create table 表名 
select 查询列表 from 旧表【where 筛选】;

### 2、常见数据类型介绍  √ 

一、数值型
1、整型
tinyint、smallint、mediumint、int/integer、bigint
1         2        3          4            8

特点：
①都可以设置无符号和有符号，默认有符号，通过unsigned设置无符号
②如果超出了范围，会报out or range异常，插入临界值
③长度可以不指定，默认会有一个长度
长度代表显示的最大宽度，如果不够则左边用0填充，但需要搭配zerofill，并且默认变为无符号整型


2、浮点型
定点数：decimal(M,D)
浮点数:
	float(M,D)   4
	double(M,D)  8

特点：
①M代表整数部位+小数部位的个数，D代表小数部位
②如果超出范围，则报out or range异常，并且插入临界值
③M和D都可以省略，但对于定点数，M默认为10，D默认为0
④如果精度要求较高，则优先考虑使用定点数

二、字符型
char、varchar、binary、varbinary、enum、set、text、blob

char：固定长度的字符，写法为char(M)，最大长度不能超过M，其中M可以省略，默认为1
varchar：可变长度的字符，写法为varchar(M)，最大长度不能超过M，其中M不可以省略

三、日期型
year年
date日期
time时间
datetime 日期+时间          8      
timestamp 日期+时间         4   比较容易受时区、语法模式、版本的影响，更能反映当前时区的真实时间         

### 3、常见约束  	  √

一、常见的约束
NOT NULL：非空，该字段的值必填
UNIQUE：唯一，该字段的值不可重复
DEFAULT：默认，该字段的值不用手动插入有默认值
CHECK：检查，mysql不支持
PRIMARY KEY：主键，该字段的值不可重复并且非空  unique+not null
FOREIGN KEY：外键，该字段的值引用了另外的表的字段

主键和唯一
1、区别：
①、一个表至多有一个主键，但可以有多个唯一
②、主键不允许为空，唯一可以为空
2、相同点
都具有唯一性
都支持组合键，但不推荐
外键：
1、用于限制两个表的关系，从表的字段值引用了主表的某字段值
2、外键列和主表的被引用列要求类型一致，意义一样，名称无要求
3、主表的被引用列要求是一个key（一般就是主键）
4、插入数据，先插入主表
删除数据，先删除从表
可以通过以下两种方式来删除主表的记录
#方式一：级联删除
ALTER TABLE stuinfo ADD CONSTRAINT fk_stu_major FOREIGN KEY(majorid) REFERENCES major(id) ON DELETE CASCADE;

#方式二：级联置空
ALTER TABLE stuinfo ADD CONSTRAINT fk_stu_major FOREIGN KEY(majorid) REFERENCES major(id) ON DELETE SET NULL;



二、创建表时添加约束
create table 表名(
	字段名 字段类型 not null,#非空
	字段名 字段类型 primary key,#主键
	字段名 字段类型 unique,#唯一
	字段名 字段类型 default 值,#默认
	constraint 约束名 foreign key(字段名) references 主表（被引用列）

)
注意：
			支持类型		可以起约束名			
列级约束		除了外键		不可以
表级约束		除了非空和默认	可以，但对主键无效

列级约束可以在一个字段上追加多个，中间用空格隔开，没有顺序要求



三、修改表时添加或删除约束
1、非空
添加非空
alter table 表名 modify column 字段名 字段类型 not null;
删除非空
alter table 表名 modify column 字段名 字段类型 ;

2、默认
添加默认
alter table 表名 modify column 字段名 字段类型 default 值;
删除默认
alter table 表名 modify column 字段名 字段类型 ;
3、主键
添加主键
alter table 表名 add【 constraint 约束名】 primary key(字段名);
删除主键
alter table 表名 drop primary key;

4、唯一
添加唯一
alter table 表名 add【 constraint 约束名】 unique(字段名);
删除唯一
alter table 表名 drop index 索引名;
5、外键
添加外键
alter table 表名 add【 constraint 约束名】 foreign key(字段名) references 主表（被引用列）;
删除外键
alter table 表名 drop foreign key 约束名;



四、自增长列
特点：
1、不用手动插入值，可以自动提供序列值，默认从1开始，步长为1
auto_increment_increment
如果要更改起始值：手动插入值
如果要更改步长：更改系统变量
set auto_increment_increment=值;
2、一个表至多有一个自增长列
3、自增长列只能支持数值型
4、自增长列必须为一个key

一、创建表时设置自增长列
create table 表(
	字段名 字段类型 约束 auto_increment
)
二、修改表时设置自增长列
alter table 表 modify column 字段名 字段类型 约束 auto_increment
三、删除自增长列
alter table 表 modify column 字段名 字段类型 约束 			

## 八、TCL语言的学习

### 	事务和事务处理 

### 一、 含义
事务：一条或多条sql语句组成一个执行单位，一组sql语句要么都执行要么都不执行
### 二、特点（ACID）
A 原子性：一个事务是不可再分割的整体，要么都执行要么都不执行
C 一致性：一个事务可以使数据从一个一致状态切换到另外一个一致的状态
I 隔离性：一个事务不受其他事务的干扰，多个事务互相隔离的
D 持久性：一个事务一旦提交了，则永久的持久化到本地

### 三、事务的使用步骤 ★
了解：
隐式（自动）事务：没有明显的开启和结束，本身就是一条事务可以自动提交，比如insert、update、delete
显式事务：具有明显的开启和结束

使用显式事务：
①开启事务
set autocommit=0;
start transaction;#可以省略

②编写一组逻辑sql语句
注意：sql语句支持的是insert、update、delete

设置回滚点：
savepoint 回滚点名;

③结束事务
提交：commit;
回滚：rollback;
回滚到指定的地方：rollback to 回滚点名;
### 四、并发事务
1、事务的并发问题是如何发生的？
多个事务 同时 操作 同一个数据库的相同数据时
2、并发问题都有哪些？
脏读：一个事务读取了其他事务还没有提交的数据，读到的是其他事务“更新”的数据
不可重复读：一个事务多次读取，结果不一样
幻读：一个事务读取了其他事务还没有提交的数据，只是读到的是 其他事务“插入”的数据
3、如何解决并发问题
通过设置隔离级别来解决并发问题
4、隔离级别
					脏读		不可重复读		幻读
read uncommitted:读未提交     ×                ×              ×        
read committed：读已提交      √                ×              ×
repeatable read：可重复读     √                √              ×
serializable：串行化          √                √              √        