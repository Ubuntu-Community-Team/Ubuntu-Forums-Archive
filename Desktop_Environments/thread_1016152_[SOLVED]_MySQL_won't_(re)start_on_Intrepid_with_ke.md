---
title: "[SOLVED] MySQL won't (re)start on Intrepid with kernel 2.6.27-9"
date: 2008-12-19
forum: Desktop Environments
---

### Post by stefanadelbert on 2008-12-19
I installed the LAMP stack on Intrepid (2.6.26-7) and it all works very well. But since upgrading to kernel 2.6.27-9, MySQL does not run. When I try restarting I get the following:
```
stefan@stefan-laptop:/boot$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                      [ OK ]
 * Starting MySQL database server mysqld                      [fail]
```
When I try starting a mysql session, I get:
```
stefan@stefan-laptop:/boot$ sudo mysql -uroot
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```
There is nothing in 'dmesg' and I just don't know where to start looking to solve the problem. Can anyone please shed some light?

Thanks
Stef

---

### Post by stefanadelbert on 2008-12-20
It suddenly started working. I don't think I did anything that would have caused it to start working.

Anyway, all good now. Would still be good to know where to look for mysql related logs/erros to help. I've found /var/log/mysql.log. Any other tips?

---

