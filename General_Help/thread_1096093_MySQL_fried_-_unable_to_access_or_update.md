---
title: "MySQL fried - unable to access or update"
date: 2009-03-14
forum: General Help
---

### Post by cditty on 2009-03-14
I don't know what I did or how I did it, but now my mysql server is hosed.  I am completely unable to log into the mysql server and I cannot upgrade it or remove it to reinstall it.

Searching through the forums, I have tried everything I found and nothing works.  Here is my daemon.log.
```
Mar 14 11:49:00 Enterprise mysqld_safe[5865]: started
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: The log sequence number in ibdata files does not match
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: the log sequence number in the ib_logfiles!
Mar 14 11:49:00 Enterprise mysqld[5869]: 090314 11:49:00  InnoDB: Database was not shut down normally!
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: Starting crash recovery.
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: Reading tablespace information from the .ibd files...
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: Restoring possible half-written data pages from the doublewrite
Mar 14 11:49:00 Enterprise mysqld[5869]: InnoDB: buffer...
Mar 14 11:49:01 Enterprise mysqld[5869]: 090314 11:49:01  InnoDB: Started; log sequence number 0 16319151
Mar 14 11:49:01 Enterprise mysqld[5869]: 090314 11:49:01 [Note] /usr/sbin/mysqld: ready for connections.
Mar 14 11:49:01 Enterprise mysqld[5869]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5945]: Upgrading MySQL tables if necessary.
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5953]: Looking for 'mysql' in: /usr/bin/mysql
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5953]: Looking for 'mysqlcheck' in: /usr/bin/mysqlcheck
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5953]: Running 'mysqlcheck'...
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5953]: /usr/bin/mysqlcheck: Got error: 1045: Access denied for user 'debian-sys-maint'@'l
ocalhost' (using password: YES) when trying to connect
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[5953]: FATAL ERROR: Upgrade failed
Mar 14 11:49:02 Enterprise /etc/mysql/debian-start[6008]: Checking for insecure root accounts.
Mar 14 12:20:26 Enterprise mysqld_safe[5917]: started
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: The log sequence number in ibdata files does not match
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: the log sequence number in the ib_logfiles!
Mar 14 12:20:26 Enterprise mysqld[5921]: 090314 12:20:26  InnoDB: Database was not shut down normally!
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: Starting crash recovery.
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: Reading tablespace information from the .ibd files...
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: Restoring possible half-written data pages from the doublewrite
Mar 14 12:20:26 Enterprise mysqld[5921]: InnoDB: buffer...
Mar 14 12:20:27 Enterprise mysqld[5921]: 090314 12:20:27  InnoDB: Started; log sequence number 0 16319151
Mar 14 12:20:27 Enterprise mysqld[5921]: 090314 12:20:27 [Note] /usr/sbin/mysqld: ready for connections.
Mar 14 12:20:27 Enterprise mysqld[5921]: Version: '5.0.67-0ubuntu6'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Mar 14 12:20:40 Enterprise /etc/init.d/mysql[6504]: 1 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' r
esulted in
Mar 14 12:20:40 Enterprise /etc/init.d/mysql[6504]: /etc/rc2.d/S50mysql: line 75: /usr/bin/mysqladmin: No such file or directory
Mar 14 12:20:40 Enterprise /etc/init.d/mysql[6504]: 
Mar 14 12:25:51 Enterprise mysqld_safe[7664]: A mysqld process already exists
Mar 14 12:26:06 Enterprise /etc/init.d/mysql[7844]: 1 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' r
esulted in
Mar 14 12:26:06 Enterprise /etc/init.d/mysql[7844]: /etc/init.d/mysql: line 75: /usr/bin/mysqladmin: No such file or directory
Mar 14 12:26:06 Enterprise /etc/init.d/mysql[7844]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: /usr/bin/mysqladmin -u root -h Enterprise password 'new-password'
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: Alternatively you can run:
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: /usr/bin/mysql_secure_installation
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: which will also give you the option of removing the test
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: databases and anonymous user created by default.  This is
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: strongly recommended for production servers.
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: See the manual for more instructions.
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: Please report any problems with the /usr/bin/mysqlbug script!
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: 
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: The latest information about MySQL is available on the web at
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: http://www.mysql.com
Mar 14 13:02:12 Enterprise mysqld_safe[9668]: Support MySQL by buying support/licenses at http://shop.mysql.com
Mar 14 13:02:13 Enterprise mysqld_safe[9729]: ERROR: 1046  No database selected
Mar 14 13:02:13 Enterprise mysqld_safe[9729]: 090314 13:02:13 [ERROR] Aborting
Mar 14 13:02:13 Enterprise mysqld_safe[9729]: 
Mar 14 13:02:13 Enterprise mysqld_safe[9729]: 090314 13:02:13 [Note] /usr/sbin/mysqld: Shutdown complete
Mar 14 13:02:13 Enterprise mysqld_safe[9729]: 
Mar 14 13:02:14 Enterprise /etc/init.d/mysql[9830]: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz

```

I get error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)' errors and I've looked in the /etc/mysql/debian.cnf file for the password.  The password that is there still returns a access denied.  

I've tried going into the Synaptic Package manager and removing it, but it fails with an error (1).

Any someone help me so I can get my system back to normal?

Thanks
Chris

---

