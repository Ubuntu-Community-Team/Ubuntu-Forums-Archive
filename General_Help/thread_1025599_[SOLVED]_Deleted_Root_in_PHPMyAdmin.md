---
title: "[SOLVED] Deleted Root in PHPMyAdmin"
date: 2008-12-30
forum: General Help
---

### Post by pmiln099 on 2008-12-30
I've searched previous threads on this topic, but have found no workable answer for me. I was in the priveleges tab in phpmyadmin, checked the three "root" accounts and stupidly clicked "go" which deleted them. I have a MYSQL database that I need and now cannot access. Can anyone please walk me through the steps required to either (a) create a new root user or (b) somehow save the tables from mysql and then reinstall mysql. I need some fairly detailed, step-by-step instructions for either, or both, solutions.
Using Ubuntu 8.04 and Mysql 5.0.

Thanks!

---

### Post by Titan8990 on 2008-12-30
Are you sure that the root accnt is actually delete?


What happens if you do:

mysql -u root -p

---

### Post by pmiln099 on 2008-12-30
> **Titan8990 said:**
> Are you sure that the root accnt is actually delete?


What happens if you do:

mysql -u root -p

I get the message: Access denied for user 'root'@'localhost' (using password: YES)
If I leave the out the password (mysql -u root) it logs in. But no priveleges.

---

### Post by iponeverything on 2008-12-30
This might help you out:
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

### Post by pmiln099 on 2008-12-30
> **iponeverything said:**
> This might help you out:
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

Very nice instructions. Unfortunately, doesn't work. Final step in the instructions to test new password gives me the same :Access denied for user 'root'@'localhost' (using password:YES).

My problem isn't with the password, it's with the privileges.

---

### Post by pmiln099 on 2009-01-05
SOLVED!! Code as follows:
>sudo /etc/init.d/mysql stop
>sudo mysqld --skip-grant-tables &
>mysql
mysql>use mysql;
mysql>INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>INSERT INTO user VALUES ('mycomputername','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>flush privileges;
mysql>quit
>sudo killall mysqld
>sudo /etc/init.d/mysql start

---

### Post by tareko on 2009-01-19
God bless you. It hurts me to think of what might have happened if I had this problem 2 weeks ago instead of today.

And just to make this solution future proof, this is how to make the above (I had to since I'm using a different version of mysql):

```

use mysql;
desc user;

```

Essentially, fill in with 'y' as many times as necessary, and put the host and username where desired.

tarek ; )

---

### Post by cariboo on 2009-01-19
An easier way might have been to just run:

```
dpkg-reconfigure mysql-server-5.0
```

then just a new password when prompted.

I always like to create another user just in case.

In the mysql console type:

```
grant all privileges on *.* to <user>@'localhost'
indentified by '<password>' with grant option;

grant all privileges on *.* to <user>@'%'
identified by '<password>' with grant option;
```

The <user>@'%' allows you to access the database remotely

---

### Post by zmartant on 2009-11-24
> **pmiln099 said:**
> SOLVED!! Code as follows:
>sudo /etc/init.d/mysql stop
>sudo mysqld --skip-grant-tables &
>mysql
mysql>use mysql;
mysql>INSERT INTO user VALUES ('localhost','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>INSERT INTO user VALUES ('127.0.0.1','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>INSERT INTO user VALUES ('mycomputername','root',password('newpassword'),'Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','Y','','','','',0,0,0,0);
mysql>flush privileges;
mysql>quit
>sudo killall mysqld
>sudo /etc/init.d/mysql start

You are awesome.  I managed to delete the root configurations while using PHPMyADMIN and could not log back in.  I tried to uninstall and re-install MySQL without avail. I could not reset the root password, due to the root configurations had been deleted.  I did not know enough MySQL commands to replace what was deleted.  I used PHPMyADMIN when ever I needed to interact with MySQL.  Your remedy resolved my issue.  I am now studying MySQL......[-o< Thank you!

---

