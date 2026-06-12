---
title: "MySQL init.d scripts not installed with mysql5 package."
date: 2009-04-20
forum: General Help
---

### Post by mallyone on 2009-04-20
Basically I've installed an apache/php/mysql on a vanilla box, everything is working, but the mysql init.d scripts were not dropped in init.d.  

I found the scripts here:
/usr/share/mysql-common/internal-use-only/

-rw-r--r-- 1 root root 5.7K Feb  3 16:15 _etc_init.d_mysql
-rw-r--r-- 1 root root  837 Feb  3 16:15 _etc_logrotate.d_mysql-server
-rw-r--r-- 1 root root 1.2K Feb  3 16:15 _etc_mysql_debian-start

I'm wondering if someone smarter than I could tell me if I can copy them over as is, or if I should try to reinstall?

Thanks in advance.
Malcolm.

---

### Post by mallyone on 2009-04-20
ummmm, in true bonehead fashion... MySQL was not installed... [long excuse goes here].

:) m...

---

### Post by Thyme on 2009-04-20
hehe :) It happens to the best of us !

---

