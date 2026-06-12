---
title: "problem with mysql updates on 8.04 -- with a twist"
date: 2009-04-15
forum: General Help
---

### Post by commonplace on 2009-04-15
Running 8.04 LTS server edition. Trying to install automatic updates, and it keeps failing on the MySQL upgrade.

This is the error from the apt log:

```
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.3 (using .../mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb) ...
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld
   ...done.
^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
```


Researching this through the forums, I found that I just need to change the MySQL password for the debian-sys-maint account to match the password found in /etc/mysql/debian.cnf

No problem... except when I went into phpMyAdmin to change the password for that user, there isn't a user with that name. There's no debian-sys-maint user at all. Do I need to add one? Why wouldn't there be one?

These updates seem scary to me. :)  Removing MySQL, Apache, etc. to replace them with updated ones. I'm scared it's going to break the web site that's running on this server. Guess I'll say a prayer!

So, anyone know why I'm missing the debian-sys-maint user and how I can resolve this and install the updates? Thanks!

/Kevin

---

### Post by commonplace on 2009-04-15
Got tired of waiting for a response -- I'm impatient -- and went ahead and created a new user called debian-sys-maint in MySQL. Gave it the password specified in /etc/mysql/debian.cnf and granted *.* access to the account.

Ran sudo apt-get upgrade and installed all the updates, and everything went fine.

/Kevin

---

