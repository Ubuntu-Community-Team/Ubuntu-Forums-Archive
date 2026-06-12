---
title: "MYSQL problems"
date: 2006-08-17
forum: Desktop Environments
---

### Post by GhandiBurger on 2006-08-17
I used the Synaptic Package Manager to install MYSQL, however I don't think it installed right because I get this error when running "sudo mysql"

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

How can I fix this?

---

### Post by meng on 2006-08-17
Which mysql package did you install (there are many).
You probably need to have mysqld (sever) running before you run mysql (client).

---

### Post by GhandiBurger on 2006-08-18
I installed 5.0.22. How do I get mysqld running?

---

### Post by meng on 2006-08-18
Not just the version - did you install the client or the server package? Do you remember the package name?

---

### Post by GhandiBurger on 2006-08-18
both client and server are installed. names: mysql-server and mysql-client-5.0

---

### Post by meng on 2006-08-18
mysqld is the server

Try the following:
ps aux | grep mysqld
to see if there are any processes named mysqld

If not, then
sudo mysqld

Then
mysql

---

