---
title: "MySQL Fails to start."
date: 2009-02-19
forum: General Help
---

### Post by Slyke on 2009-02-19
Hey, didn't know if this is the correct place, so please move it one of the mods if it's not :).

My problem is that MySQL fails to start when I try:
/etc/init.d/mysql restart
or
/etc/init.d/mysql start

Just says [fail] in the right hand corner of the screen.

Stop works fine.

Yet I can run commands like:
mysql -u root

and MySQL client will start up and work fine.

Here is what happens when I run MySQL and some commands:
[PHP]
mysql> show variables like 'basedir';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| basedir       | /usr/ | 
+---------------+-------+
1 row in set (0.00 sec)

mysql> show variables like 'datadir';
+---------------+-----------------+
| Variable_name | Value           |
+---------------+-----------------+
| datadir       | /var/lib/mysql/ | 
+---------------+-----------------+
1 row in set (0.01 sec)
[/PHP]

I've checked the error logs, and MySQL logs, and they are both blank (/var/log/mysql.err and var/log/mysql.log). Initially I had to change the permission for both these files as they were owned and writable only by root.

If you need the my.cnf file I'll post it up, but it's a little long!

---

