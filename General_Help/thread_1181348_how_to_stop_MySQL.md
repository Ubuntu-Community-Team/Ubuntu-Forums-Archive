---
title: "how to stop MySQL"
date: 2009-06-07
forum: General Help
---

### Post by aniketto on 2009-06-07
Hi all,
I want to stop MySQL for sonfugration of some other things.
I used the command,
***sudo /etc/init.d/mysql stop***
but it gave me error 
**** Stopping MySQL database server mysqld [fail]***
 
Can anybody please tell me *wh*at could be the reason and how to resolve it.

---

### Post by infallible on 2009-06-07
just to throw something out there, my next step would be

sudo /etc/init.d/mysql status

---

### Post by tgalati4 on 2009-06-07
Perhaps there are errors that show up in /var/log/mysql.err or mysql.log.

---

### Post by aniketto on 2009-06-07
> **infallible said:**
> just to throw something out there, my next step would be
 
sudo /etc/init.d/mysql status
When I executed above command it gave me error as below.
 
>  
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'


---

### Post by aniketto on 2009-06-08
I solved the MySQL stop failed problem using [http://mirzmaster.wordpress.com/2009/01/16/mysql-access-denied-for-user-debian-sys-maintlocalhost/](http://mirzmaster.wordpress.com/2009/01/16/mysql-access-denied-for-user-debian-sys-maintlocalhost/)

---

### Post by tgalati4 on 2009-06-08
Glad you solved the problem.  This note should be included in the upgrade/changelog notes for mysql whenever it gets upgraded.

---

