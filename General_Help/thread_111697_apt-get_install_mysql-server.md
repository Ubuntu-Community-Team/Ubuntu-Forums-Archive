---
title: "apt-get install mysql-server"
date: 2006-01-02
forum: General Help
---

### Post by Adam Atlas on 2006-01-02
I'm trying to apt-get install mysql-server, and it's insisting Postfix be installed in addition. Just why would Postfix be a dependency for MySQL? And, since I am using qmail instead of Postfix, how can I install mysqld without Postfix?

---

### Post by socrazy143 on 2006-01-02
Have you already installed qmail?

mysql-server depends on postfix to tell you about problems.  You may want to skip aptitude and just compile your own mysql.  It really isn't that hard to do.

Simply download the tarball to /tmp, unpack it.  I believe you have to run ./configure first (of course cd into the folder) then run make, make install and you should be good to go.

Others with more mysql experience should chime in on this one.

---

