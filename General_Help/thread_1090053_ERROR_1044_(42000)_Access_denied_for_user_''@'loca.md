---
title: "ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'"
date: 2009-03-07
forum: General Help
---

### Post by AudioMove on 2009-03-07
I'm trying to follow the instructions at [http://dev.mysql.com/doc/refman/4.1/en/default-privileges.html](http://dev.mysql.com/doc/refman/4.1/en/default-privileges.html) to secure mysql after installation on Ubuntu Server.

I entered sudo mysql -u admin at the command prompt and enter 
mysql> SET PASSWORD FOR ''@'localhost' = PASSWORD('newpwd');

The following error occurs:
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'

I ensured the mysql serevr has started. Entering hostname at the command prompt shows as ubuntu (does that make a difference?).

I've search all over the net to try correct this but cannot find a solution.

---

### Post by Iowan on 2009-03-07
I must be missing something (not unusual)... '' would not seem top be a valid user.

---

