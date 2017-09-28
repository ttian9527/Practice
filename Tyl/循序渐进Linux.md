#循序渐进Linux 
----

Pracitice **user:**	`tyl`	**password:**	`root`
   
To boot Ubuntu 16.04 Desktop without X one time, add `systemd.unit=multi-user.target` to the `linux` command line in GRUB.

To make this the default, use  

>`sudo systemctl set-default multi-user.target`  

To return to default booting into X, use 

>`sudo systemctl set-default graphical.target`  

To see the current default target,

>`sudo systemctl get-default`


##shell 命令的语法

###1格式

`command [options] [arguments]`  

* command:表示命令的名称.  
* options:表示命令的选项.  
* arguments:表示命令的参数

>一般在`options`前面加`-`以区别`arguments`  
>`-options`可以有多个,可以单独列出,也可以全部列出  
>
>>`ls -a -l` == `ls -al`
>  
>在一行中可以输入多个命令,用分号`;`分开
>
>>`ls -al;cp file1.txt file2.txt`
>
>可以由多行输入组成一个命令,用`\`连接
>
>>```
>> >	cp -i \
>> >	file1.txt \
>> >	file2.txt
>>```  

###2通配符

bash中常用的通配符`*`,`?`,`[]`.  

> 1. `*` 匹配任意字符除了`.`  
> 2. `?` 匹配任意单字符  
> 3. `[]` 匹配任意区间内字符  
>	* `[12345]`==`[1-5]`  
>		匹配1-5的任意一个  
> 4. 任意组合 

###3重定向

标准输入,标准输出,错误输出的重定向.  

####标准输入

>`<`,	`<<`  
>>`<`后接文件,文件内容作为输入.  
>>`<<`后接任意分隔号.以空格或回车结束,两个分隔号之间的内容为输入.
>>>```
>>>$ wc << aa abcdefg aa
>>>```  
>
>>上面`abcdefg`作为输入

####标准输出  

>`>`,	`>>`
>>`>`后接文件名,将使命令输出内容输出到文件中,文件不存在时会新建,已有内容时覆盖源文件,   
>>`>>`后接文件名,将会使输出内容接着文件内容写入文件.

####错误输出

>`2>`,	`>>`
>>同标准输出相同  

###shell的管道

用`|`符号连接命令,使该符号前一个命令的输出成为后一命令的输入
>`$ ls -a | more` 分屏显示当前文件夹内容



  
`$ lspci`	列出PCI设备  	
`$ systemctl` 服务管理,电源管理.  

>`$ systemctl start httpd.service` 启动httpd服务  
>`$ systemctl poweroff`  关机

`$ shutdown`电源管理,_关机,重启_  
