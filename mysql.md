# 解决办法 1

卸载完全，删除所有数据,先关闭跟MySql所有有关的进程,进入命令行(cmd)中输入taskkill /f /im mysqld-nt.exe

然后找到MySql的根目录删除即可

# 解决办法 2

在命令行里面输出密码或者更更改密码

.在命令行运行：taskkill /f /im mysqld-nt.exe

下面的操作是操作mysql中bin目录下的一些程序，如果没有配置环境变量的话，需要切换到mysql的bin 目录下执行如下语句。不然无效

.继续在命令行运行：mysqld-nt --skip-grant-tables

# 解决办法3

新开一个命令行运行：mysql -u root   （如果没有配置mysql的bin环境变量的话需要切换到bin目录下执行此语句）

如果不想改密码，只是想看原来的密码的话。可以在命令行执行这个语句

select host,user,password from mysql.user;//即可查看到用户和密码
如果要修改密码的话，在命令行下执行下面的语句

update mysql.user set password='这里填写你要设置的密码' where user='root';
完成这些操作后，继续在命令行运行

taskkill /f /im mysqld-nt.exe;//安全着想，先结束，因为现在这样是可以用mysql -u root 直接登录的
net start mysql;//启动mysql服务
