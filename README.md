ssh-auto-login-manage
=====================

SSH auto login without password and managing ssh hosts list on Mac OSX & Linux.

You can use these scripts instead of SecureCRT, xshell.

Refer to [ssh-auto-login](https://github.com/liaohuqiu/ssh-auto-login) and [sshgo](https://github.com/emptyhua/sshgo).

###How to use
1. `git clone https://github.com/flying5/ssh-auto-login-manage.git`
2. Modify file `/path/to/ssh-auto-login-manage/hosts`, use your hosts, you can set the special username & password & id_file for each hostname, and support the split with blankspace:

    ```
    deploy
        1.1.1.1  user1  password1
        2.2.2.2  user2  #use Public key authentication
        3.3.3.3  user3 -i /path/to/id_file.pem  #use id file to login
    Online-1
        4.4.4.4 user password #the first node will default as the below server's jumper server,if below server with section of indent
        intenal.server # below servers will use 4.4.4.4 as the jumper server
            10.0.2.10 user3 password3
            10.0.2.11 user4 password4
    Online-2
        5.5.5.5:22222 user5 password5 #use the special port
        6.6.6.6 user6 password6
    ```
3. Run script `./sshgo`, or you can alias `sshgo` command, add the line to the end of ~/.bash_profile and source it:
 * alias sshgo='/path/to/ssh-auto-login-manage/sshgo'
5. enjoy the `sshgo`.

###screenshot
![screenshot](https://github.com/upton/ssh-auto-login-manage/blob/master/screenshot.png)

-----
### 说明

* ssh免密码自动登录和主机管理，可以替代SecureCRT的自动登录。
* Mac下的term功能较弱，无法提供像SecureCRT那样方便的主机管理和自动登录功能。在网上找到用expect做自动登录的项目ssh-auto-login，和一个用python写的主机管理界面，于是把两个工程合并在一起，就是现在这个工程了。
* 参考了 [ssh-auto-login](https://github.com/liaohuqiu/ssh-auto-login) and [sshgo](https://github.com/emptyhua/sshgo)

-----
### update

* 支持通过多级目录的方式管理server（之前版本在多级目录下，会默认为需要使用jumper server）。
* jumper server功能得到保留。在编辑hosts文件时，server前加上`*`号，可继续之前版本的jumper server功能。