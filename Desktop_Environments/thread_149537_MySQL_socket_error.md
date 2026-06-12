---
title: "MySQL socket error"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Blairboy on 2006-03-24
Using dovecot, I have commented out the db_unix_socket line in dovecot-mysql.conf.  I still get this error when I try to log into the server.

Mar 24 03:25:05 localhost dovecot-auth: MySQL: Can't connect to database maildb: Can't connect to local MySQL server through socket '/var/tmp/mysql.sock' (2)
Mar 24 03:25:05 localhost pop3-login: Aborted login [192.168.1.1]

Any ideas on why it's still trying to use a socket as opposed to just localhost?

---

### Post by Blairboy on 2006-03-24
Just out of curiousity, why is it that no one even reads my posts?

---

### Post by bennybobw on 2006-03-27
I don't know if this helps or not, but read the end of this post where they were discussing socket vs. localhost issues.
[http://www.ubuntuforums.org/showthread.php?t=93725]("http://www.ubuntuforums.org/showthread.php?t=93725")

---

