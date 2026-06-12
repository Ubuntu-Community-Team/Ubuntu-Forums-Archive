---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2008-12-12
forum: General Help
---

### Post by nshiell on 2008-12-12
Hi
I have a serious problem with MySQL.
I know there r allot of threads floating around about this but none of them have helped me and I'm out of ideas.

I installed MySQl client/server through apt-get and it all worked ok. Then I stupidly moved some of the MySQl dirs around (on to a data harddrive). I have moved them back now, but i still get the error: -

[B]mysql -uroot
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[/B]

I have tried evrything I can and I'm out of ideas, can u help me?
Tnx.

---

### Post by LoneWolfJack on 2008-12-12
try

```
sudo /etc/init.d/mysql start
```

---

### Post by nshiell on 2008-12-13
Hi thanks for helping.
I ran "**sudo /etc/init.d/mysql start**"
and got: -
** * Starting MySQL database server mysqld                                 [fail]**

What do u belive should be my nexty step?
Tnx.

---

### Post by LoneWolfJack on 2008-12-13
do you happen to run plesk?

if so:

```

sudo /etc/init.d/psa stop
sudo /etc/init.d/psa start

```

if not, check your mysql error log to see why mysql fails to start. you can probably find the error log in /etc/apache2 and it's called... well.. error.log

---

### Post by ju2wheels on 2008-12-13
Just another thing to consider... did you move the MySQL folders around on the same hard drive or across partitions with different file systems? Transferring them between different file systems could lose folder permissions and could affect the ability of the application to open the file socket if the permissions are wrong.

---

