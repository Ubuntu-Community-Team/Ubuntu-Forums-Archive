---
title: "#2002 - The server is not responding (or the local MySQL server's socket is not corre"
date: 2005-12-17
forum: General Help
---

### Post by slempl on 2005-12-17
i'm new with linux... small php developer and i need phpmyadmin, so i've installed it and during the instalation all went smoothly till the end.. at the end i got the error and i just crossed it with my eyes. I started the localhost/phpmyadmin/  
it's running and asking me for username and pass....
as default user: root   and password empty....
when i try to log in i get this....    #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)....


Please help.... my boss is going to kill me if i dont continue working soon!  :(

THANKS!

---

### Post by kosmic on 2005-12-17
In the Terminal do :
 
ps ax | grep mysql
 
and see if it shows up anything, if not then do :
 
sudo /etc/init.d/mysqld restart 
 
and post where what it says.

---

### Post by slempl on 2005-12-17
1534 pts/0    S+     0:00 grep mysql
i've got this after entering ps ax | grep mysql

i've entered this:  root@zverka:/# sudo /etc/init.d/mysqld restart
and i've got this: sudo: /etc/init.d/mysqld: command not found


Installation was from official site of ubuntu....[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by kosmic on 2005-12-17
Hum your mysql server is not runing.
 
 
did you do this ?
 
```
sudo apt-get install mysql-server
mysqladmin -u root password db_user_password

```
 
 
also don't forget to change HOARY to BREEZY in the repos

---

### Post by slempl on 2005-12-17
Just did it.....     ok that is a...  progress.....    entered those two lines and now it's a new error   :D lol 


#1045 - Access denied for user: 'root@localhost' (Using password: NO)

---

### Post by kosmic on 2005-12-17
when you install the mysql-server package it should ask you to assign a password to the root account, this is the root account of mysql not your linux root account.
 
 
easy way..do you have synaptic installed are you running gnome ? if yes fire up synpatic and select mysql and do remove all, after that install mysql mysqld mysql-server etc from synaptic again...and it should work out of the box.
 
 
Sorry but im not in front of a Linux box right now, I have to remember from my head :(

---

### Post by slempl on 2005-12-17
sergio@zverka:~$ sudo apt-get install mysql-server
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libmysqlclient14 mysql-client
Suggested packages:
  mysql-doc
Recommended packages:
  libmysqlclient14-dev
The following NEW packages will be installed:
  libdbd-mysql-perl libmysqlclient14 mysql-client mysql-server
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5575kB of archives.
After unpacking 13,5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
Selecting previously deselected package libmysqlclient14.
(Reading database ... 66544 files and directories currently installed.)
Unpacking libmysqlclient14 (from .../libmysqlclient14_4.1.12-1ubuntu3_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_2.9007-1_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_4.0.24-10ubuntu2_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_i386.deb) ...
Setting up libmysqlclient14 (4.1.12-1ubuntu3) ...

Setting up libdbd-mysql-perl (2.9007-1) ...
Setting up mysql-client (4.0.24-10ubuntu2) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
Checking for crashed MySQL tables in the background.
[COLOR="Red"]
sergio@zverka:~$ mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
sergio@zverka:~$ sudo -s
root@zverka:~# mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'
root@zverka:~# mysqladmin -u root password db_user_password
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'[/COLOR]

and funny, it never asked me for username and pass....  i know there is no conection betwen system and mysql root  :D


did all that you said and now i get this....    thanks!
hope you'll be able to help me...   :)

---

### Post by kosmic on 2005-12-17
do this :
 
**mysql -u root**
**SET PASSWORD FOR ''@'localhost' = PASSWORD('*newpwd*');**
**SET PASSWORD FOR ''@'*host_name*' = PASSWORD('*newpwd*');**
 
 
ps.: Do you have your root account activated ? if not do sudo passwd first

---

### Post by slempl on 2005-12-17
sergio@zverka:~$ sudo passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
sergio@zverka:~$ mysql -u root
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)


nothing.... :(

---

### Post by kosmic on 2005-12-17
hum we have a very big problem, because mysql assigned a password to the root user and we don't know what it is :(
 
1 º solution (hope it helps)
 
1 - sudo apt-get --purge remove mysql-server mysql-client 
 
2 - sudo apt-get install mysql-server mysql-cliente
 
ATTENTION - Now it should ask you to assign a password to the mysql root user
 
Then do the steps posted above

---

### Post by slempl on 2005-12-17
root@zverka:/# sudo apt-get --purge remove mysql-server mysql-client
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mysql-client* mysql-server*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 10,0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 66776 files and directories currently installed.)
Removing mysql-server ...
Stopping MySQL database server: mysqld.
Purging configuration files for mysql-server ...
Removing mysql-client ...
root@zverka:/# sudo apt-get install mysql-server mysql-client
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  mysql-doc
The following NEW packages will be installed:
  mysql-client mysql-server
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3968kB of archives.
After unpacking 10,0MB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package mysql-client.
(Reading database ... 66568 files and directories currently installed.)
Unpacking mysql-client (from .../mysql-client_4.0.24-10ubuntu2_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_i386.deb) ...
Setting up mysql-client (4.0.24-10ubuntu2) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
Checking for crashed MySQL tables in the background.




as you see it doesen't require any username or password.   :(



but default     root and no pass works...    :)  thank you very very very much....

---

### Post by slempl on 2005-12-17
I was never more happy to see phpmyadmin window
:D
thanks dude .....    you're the best...   lol

---

### Post by kosmic on 2005-12-17
Glad to help out :)

---

### Post by square_monkey on 2008-06-12
Thanks very much - very useful indeed.

---

