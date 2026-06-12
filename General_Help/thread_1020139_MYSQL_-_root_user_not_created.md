---
title: "MYSQL - root user not created?"
date: 2008-12-23
forum: General Help
---

### Post by ejunooni on 2008-12-23
I just installed mysql using the following command

```
sudo aptitude install mysql-server
```

During installation, i was asked to enter a password for root which i did but when i try to login using root, i get the following error

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


So i read a few forums and found out that there is a debian-sys-maint user

I tried logging in with this user and i was able to do that. Then i logged in using phpmyadmin to see if i can see the root user but when i go to the privileges tab, i only see the debian-sys-maint user and i cannot add more users using this debian user.


i tried reconfiguring, asks me for password again but still doesnt work

i tried to uninstall using this command

```
sudo aptitude --purge remove mysql-server
```

i thought this will remove all the configuration files but it didnt, so i tried reinstalling anyway but still having the same problem.


Any ideas whats going on here? or how i can fix this?

Thanks in advance

---

### Post by unutbu on 2008-12-23
Have you already tried this?

```
sudo dpkg-reconfigure mysql-server-5.0
```
Set a new mysql root password. For good security, do not use your Ubuntu password. 

Then type
```

mysql -u root -p

```
You will be prompted for a password.
Type in the mysql root password.
If it doesn't work please post a copy of the terminal output.

---

### Post by ejunooni on 2008-12-23
yea i have already tried this

here is the output 

$ sudo dpkg-reconfigure mysql-server-5.0

 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Stopping MySQL database server mysqld                                 [ OK ] 
Reloading AppArmor profiles : done.
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

---

### Post by tee4cute on 2008-12-23
I downloaded the mysql server installer "mysql-5.1.30-linux-i686-glibc23.tar.gz" from "www.mysql.org" directly and follow the installing instructions. It works fine!.

The one step in the installing instructions is configuring the root user by using scripts (or executable file) "scripts/mysql_install_db --user=mysql" (or "bin/mysql_install_db --user=mysql" for executable file)

("scripts/mysql_install_db" and "bin/mysql_install_db" are in the mysql folder)

This step will install the user table (contains "root" user) in the database. And then I use "mysqladmin" command to set the root password later.

I'm not sure that your case is the same?

Hope that this may help!!!

---

### Post by unutbu on 2008-12-23
How about post the output of 
```

sudo grep -a -o -e '.*root' /var/lib/mysql/mysql/user.MYD
ls -l /var/lib/mysql
cat /etc/hosts
grep bind-address /etc/mysql/my.cnf

```
The first command should show stuff like
```
	localhostroot
```
The second lists the contents of /var/lib/mysql. I'm looking for symlinks -- they don't behave as expected if you happen to use them here. (You have to edit /etc/apparmor.d/usr.sbin.mysqld in this case.)

The third command is to check that localhost resolves to 127.0.0.1.

The fourth command is to check the bind-address. 

There seems to be something unusual about your setup, so the above are just sanity checks.

---

### Post by ejunooni on 2008-12-24
Here are the ouputs. The first command didnt have any output

> emad@ebuntu:~$ sudo grep -a -o -e '.*root' /var/lib/mysql/mysql/user.MYD
[sudo] password for emad:

 
emad@ebuntu:~$ ls -l /var/lib/mysql
total 20528
-rw-r--r-- 1 mysql mysql        0 2008-12-23 21:19 debian-5.0.flag
-rw-rw---- 1 mysql mysql 10485760 2008-12-23 21:19 ibdata1
-rw-rw---- 1 mysql mysql  5242880 2008-12-24 10:44 ib_logfile0
-rw-rw---- 1 mysql mysql  5242880 2008-12-21 22:37 ib_logfile1
drwxr-xr-x 2 mysql mysql     4096 2008-12-23 21:19 mysql
-rw------- 1 mysql mysql        6 2008-12-21 22:27 mysql_upgrade_info


emad@ebuntu:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	ebuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


emad@ebuntu:~$ grep bind-address /etc/mysql/my.cnf 
bind-address		= 127.0.0.1


---

### Post by unutbu on 2008-12-24
How about try this: 
```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> use mysql;
mysql> select user,host from user where user='root' \G

```
If you see output, stop here and post the output.
If you see no output, then copy/paste this: 
```

mysql> INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('ebuntu','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>flush privileges;
mysql>quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```

---

### Post by ejunooni on 2008-12-24
Here is the output 

```
mysql> use mysql;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select user,host from mysql where user='root' \G
ERROR 1146 (42S02): Table 'mysql.mysql' doesn't exist



```

---

### Post by unutbu on 2008-12-24
Doh! my mistake. Try this instead:
```

mysql> select user,host from user where user='root' \G
```

---

### Post by ejunooni on 2008-12-24
Here you go

```
mysql> select user,host from user where user='root' \G
Empty set (0.02 sec)


```

---

### Post by ejunooni on 2008-12-27
anything guys?

any way to completely remove with all the configuration files and do a fresh install?

---

### Post by unutbu on 2008-12-28
Have you tried all the instructions in post #7 ([http://ubuntuforums.org/showpost.php?p=6432028&postcount=7)?](http://ubuntuforums.org/showpost.php?p=6432028&postcount=7)?) The second-half should allow you to set a root password.

Note that you should change newpassword to the mysql root password you really want.

I have some reservations about this method. It should work, but it does not explain why you were not given a proper setup with a root password from the beginning. 

So here are two options:
[list]
[*]Use the instructions in post #7
[*]Purge mysql-server-5.0 and then reinstall:
```
sudo apt-get purge mysql-server-5.0
sudo apt-get install mysql-server-5.0
```
If the second method fails to work, you could still try post #7 later...

The above command is a little different from what you did in post #1. mysql-server is merely a metapackage that currently depends on mysql-server-5.0. Purging it does not purge the mysql-server-5.0 configuration files.
[/list]

---

### Post by ejunooni on 2008-12-28
i ended up uninstalling mysql-server. ALso i had to uninstall mysql-common for it to remove some config files. After reinstalling everything worked fine.

Thanks for your help

---

### Post by pearl298 on 2009-11-27
Thank you - I had a similar problem and you showed the way to get out of the hole!!

---

### Post by algosakis on 2012-08-02
This one saved me !!!1


> **unutbu said:**
> How about try this: 
```
sudo /etc/init.d/mysql stop
sudo mysqld --skip-grant-tables &
mysql
mysql> use mysql;
mysql> select user,host from user where user='root' \G

```If you see output, stop here and post the output.
If you see no output, then copy/paste this: 
```

mysql> INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql> INSERT INTO user VALUES ('ebuntu','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>flush privileges;
mysql>quit
sudo killall mysqld
sudo /etc/init.d/mysql start
```

---

