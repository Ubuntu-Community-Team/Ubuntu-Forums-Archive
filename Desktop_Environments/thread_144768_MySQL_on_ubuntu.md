---
title: "MySQL on ubuntu"
date: 2006-03-15
forum: Desktop Environments
---

### Post by thedima on 2006-03-15
I have installed MySQL on a fresh instance of ubuntu. What can I do to open port 3306 so that the db is accessible from a remote machine?

---

### Post by bjweeks on 2006-03-15
Its open by default.

---

### Post by thedima on 2006-03-15
It doesnt seem to be as I can not connect from a remote machine using MySQL Control Center

---

### Post by LoclynGrey on 2006-03-15
are you also running a firewall as that might be blocking it?

---

### Post by bjweeks on 2006-03-15
[QUOTE=thedima]It doesnt seem to be as I can not connect from a remote machine using MySQL Control Center[/QUOTE]

Well it is so you must have a router or your isp blocking it.

---

### Post by thedima on 2006-03-15
Not on ubuntu, MySQL is the only thing I have installed on it. I am trying to access the machine via an internal network and there is nothing in the way there.

---

### Post by bjweeks on 2006-03-15
[QUOTE=thedima]Not on ubuntu, MySQL is the only thing I have installed on it. I am trying to access the machine via an internal network and there is nothing in the way there.[/QUOTE]

Is it damon started?

---

### Post by kthonos on 2006-03-15
What does "ps ax | grep mysql" give?

---

### Post by thedima on 2006-03-15
[QUOTE=kthonos]What does "ps ax | grep mysql" give?[/QUOTE]

 6408 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 6449 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 6450 ?        Sl     1:14 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 6451 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld

---

### Post by Koybe on 2006-03-15
**- What if you telnet port 3306 from a client?**

**- Then are you sure you don't have this option up?**
In /etc/mysql/my.conf:
```
# Prevent network access to MySQL.
skip-networking
```

**- And finally did you give the right access on the databases :**
mysql -u root -p mysql
mysql> select * from users;        
You should see the rights for all the tables. Alternatively you can install phpmyadmin which is easier to use.
Then you need to see wheter you're able to connect from a remote host (this is from Mysql manual) :
> mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'localhost'
    ->     IDENTIFIED BY 'some_pass' WITH GRANT OPTION;
mysql> GRANT ALL PRIVILEGES ON *.* TO 'monty'@'%'
    ->     IDENTIFIED BY 'some_pass' WITH GRANT OPTION;

The accounts created by these GRANT statements have the following properties:
Two of the accounts have a username of monty and a password of some_pass. Both accounts are superuser accounts with full privileges to do anything. One account ('monty'@'localhost') can be used only when connecting from the local host. The other ('monty'@'%') can be used to connect from any other host. 

---

### Post by adamkane on 2006-03-15
!

---

### Post by Koybe on 2006-03-15
[QUOTE=adamkane]![/QUOTE]
?

---

### Post by blackrim on 2006-03-19
In your /etc/mysql/my.cnf comment out 
bind-address           = 127.0.0.1

so that it is 
#bind-address           = 127.0.0.1

that should fix it.

---

### Post by transistor on 2006-04-11
You'll need supervisor rights so use
```
sudo /etc/init.d/mysql restart
```

---

