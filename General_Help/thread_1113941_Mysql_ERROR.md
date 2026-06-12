---
title: "Mysql ERROR"
date: 2009-04-02
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-02
root@muthu-desktop:~# mysql -u root
ERROR 1045 (28000): **Access denied for user 'root'@'localhost' (using password: NO)**
root@muthu-desktop:~# 
****
how to recover this problem...

---

### Post by kpatz on 2009-04-02
> **suresh_vandiyur said:**
> root@muthu-desktop:~# mysql -u root
ERROR 1045 (28000): **Access denied for user 'root'@'localhost' (using password: NO)**
root@muthu-desktop:~# 
****
how to recover this problem...
Did you set a root password for mysql when you installed?

**mysql -u root -p**

and then enter the password when prompted.

---

### Post by suresh_vandiyur on 2009-04-03
> **kpatz said:**
> Did you set a root password for mysql when you installed?

**mysql -u root -p**

and then enter the password when prompted.
Thank u so Muchhhhhhhhhhhhhhhhhhhh...
how to use the emma mysql and then how to access the mysql other users... same problem in **emma mysql** how to reover it...
**Access denied for user 'root'@'localhost' (using password: NO)**

---

