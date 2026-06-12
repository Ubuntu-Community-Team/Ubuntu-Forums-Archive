---
title: "mysql 5.0.22 won't start"
date: 2006-06-24
forum: Desktop Environments
---

### Post by WillisBueller on 2006-06-24
hello, i ran an update last week which moved me from mysql 5.0.21 to 5.0.22 and mysql stopped working with the following error.

```
...failed or took more than 6s.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

and from my syslog

```
Jun 24 10:57:36 will-laptop /etc/init.d/mysql[6868]: 0 processes alive and '/usr
/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun 24 10:57:36 will-laptop /etc/init.d/mysql[6868]: ^G/usr/bin/mysqladmin: conn
ect to server at 'localhost' failed
Jun 24 10:57:36 will-laptop /etc/init.d/mysql[6868]: error: 'Can't connect to lo
cal MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jun 24 10:57:36 will-laptop /etc/init.d/mysql[6868]: Check that mysqld is runnin
g and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jun 24 10:57:36 will-laptop /etc/init.d/mysql[6868]:
```

anyone else having this problem?
I tried moving back to 5.0.21 but i can't seem to move mysql-common back without uninstalling everything on my computer according to synaptic.
Regards,
Willis

---

### Post by WillisBueller on 2006-06-29
noone else is having this problem? it says it came from a security update repository.

---

### Post by ruudiculus on 2006-07-31
Hi, I'm having the same problem, also after this update! Together with the problem that the dhcp3-client and dhcp3-common packages were corrupted! I had to reïnstall those to get back my server's Internet connection.

So, now mysql is acting strange. But reïnstalling it means losing all your databases and you can't do a dump because you can't get it running in the first place!

Grbl...somebody?

---

### Post by ruudiculus on 2006-07-31
I panicked but my girlfriend-nerd here, cool as always ;) , seems to have found the solution:

In /var/lib/ change the **mysql** directory ownership from root back to mysql by typing:
```
chown -R :mysql /var/lib/mysql
chown -R mysql /var/lib/mysql
```

Now, we fix the mysql logging directory and file permissions (group=adm, owner=mysql), as follows:
```
chown -R :adm /var/log/mysql
chown -R mysql /var/log/mysql
chown :adm /var/log/mysql.err
chown mysql /var/log/mysql.err
chown :adm /var/log/mysql.log
chown mysql /var/log/mysql.log
```

Finally restart mysql by typing:
```
/etc/init.d/mysql restart
```

Thanks girlfriend!
(I hope, we don't have to do this EVERY time there's an update!)

---

### Post by BatteryCell on 2006-08-02
Hm I tried those things and I still get the error when I try to start mysql. Did anybody else do something different to make it work?

---

