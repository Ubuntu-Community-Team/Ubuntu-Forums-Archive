---
title: "error with phpmyadmin"
date: 2009-02-17
forum: General Help
---

### Post by tntarcadia on 2009-02-17
hi there i was wondering if someone could help me resolve this  i am new to ubunta  and have contacted my server host which wasnt much help other than telling me to google the solution which i have many times and seems everything i tried  was not successful  i got this error  and on phpmyadmin i can not access the page  gives me socket error 

Error

MySQL said: Documentation
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
Connection for controluser as defined in your configuration failed.


```
Feb 18 02:08:09 ns20984 mysqld[13683]: 
Feb 18 02:08:09 ns20984 mysqld_safe[13715]: ended
Feb 18 02:08:21 ns20984 /etc/init.d/mysql[13846]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 02:08:21 ns20984 /etc/init.d/mysql[13846]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 02:08:21 ns20984 /etc/init.d/mysql[13846]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 02:08:21 ns20984 /etc/init.d/mysql[13846]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 02:08:21 ns20984 /etc/init.d/mysql[13846]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: To do so, start the server, then issue the following commands:
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: Alternatively you can run:
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: /usr/bin/mysql_secure_installation
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: which will also give you the option of removing the test
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: databases and anonymous user created by default.  This is
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: strongly recommended for production servers.
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: See the manual for more instructions.
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: 
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: The latest information about MySQL is available on the web at
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: http://www.mysql.com
Feb 18 02:08:23 ns20984 mysqld_safe[13925]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 02:08:23 ns20984 mysqld_safe[14000]: ERROR: 1046  No database selected
Feb 18 02:08:23 ns20984 mysqld_safe[14000]: 090218  2:08:23 [ERROR] Aborting
Feb 18 02:08:23 ns20984 mysqld_safe[14000]: 
Feb 18 02:08:23 ns20984 mysqld_safe[14000]: 090218  2:08:23 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:08:23 ns20984 mysqld_safe[14000]: 
Feb 18 02:08:23 ns20984 mysqld_safe[14127]: started
Feb 18 02:08:23 ns20984 mysqld[14130]: 090218  2:08:23  InnoDB: Started; log sequence number 0 43655
Feb 18 02:08:23 ns20984 mysqld[14130]: 090218  2:08:23 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:08:23 ns20984 mysqld[14130]: 090218  2:08:23 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:08:23 ns20984 mysqld[14130]: 090218  2:08:23 [ERROR] Aborting
Feb 18 02:08:23 ns20984 mysqld[14130]: 
Feb 18 02:08:23 ns20984 mysqld[14130]: 090218  2:08:23  InnoDB: Starting shutdown...
Feb 18 02:08:25 ns20984 mysqld[14130]: 090218  2:08:25  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:08:25 ns20984 mysqld[14130]: 090218  2:08:25 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:08:25 ns20984 mysqld[14130]: 
Feb 18 02:08:25 ns20984 mysqld_safe[14162]: ended
Feb 18 02:08:37 ns20984 /etc/init.d/mysql[14293]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 02:08:37 ns20984 /etc/init.d/mysql[14293]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 02:08:37 ns20984 /etc/init.d/mysql[14293]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 02:08:37 ns20984 /etc/init.d/mysql[14293]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 02:08:37 ns20984 /etc/init.d/mysql[14293]: 
Feb 18 02:19:30 ns20984 mysqld_safe[14392]: started
Feb 18 02:19:30 ns20984 mysqld[14395]: nohup: ignoring input
Feb 18 02:19:30 ns20984 mysqld[14395]: 090218  2:19:30  InnoDB: Started; log sequence number 0 43655
Feb 18 02:19:30 ns20984 mysqld[14395]: 090218  2:19:30 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:19:30 ns20984 mysqld[14395]: 090218  2:19:30 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:19:30 ns20984 mysqld[14395]: 090218  2:19:30 [ERROR] Aborting
Feb 18 02:19:30 ns20984 mysqld[14395]: 
Feb 18 02:19:30 ns20984 mysqld[14395]: 090218  2:19:30  InnoDB: Starting shutdown...
Feb 18 02:19:32 ns20984 mysqld[14395]: 090218  2:19:32  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:19:32 ns20984 mysqld[14395]: 090218  2:19:32 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:19:32 ns20984 mysqld[14395]: 
Feb 18 02:19:32 ns20984 mysqld_safe[14407]: ended
Feb 18 02:28:21 ns20984 mysqld_safe[14450]: started
Feb 18 02:28:21 ns20984 mysqld[14453]: nohup: ignoring input
Feb 18 02:28:21 ns20984 mysqld[14453]: 090218  2:28:21  InnoDB: Started; log sequence number 0 43655
Feb 18 02:28:21 ns20984 mysqld[14453]: 090218  2:28:21 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:28:21 ns20984 mysqld[14453]: 090218  2:28:21 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:28:21 ns20984 mysqld[14453]: 090218  2:28:21 [ERROR] Aborting
Feb 18 02:28:21 ns20984 mysqld[14453]: 
Feb 18 02:28:21 ns20984 mysqld[14453]: 090218  2:28:21  InnoDB: Starting shutdown...
Feb 18 02:28:24 ns20984 mysqld[14453]: 090218  2:28:24  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:28:24 ns20984 mysqld[14453]: 090218  2:28:24 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:28:24 ns20984 mysqld[14453]: 
Feb 18 02:28:24 ns20984 mysqld_safe[14465]: ended
Feb 18 02:30:30 ns20984 mysqld_safe[14553]: started
Feb 18 02:30:30 ns20984 mysqld[14556]: nohup: ignoring input
Feb 18 02:30:30 ns20984 mysqld[14556]: 090218  2:30:30  InnoDB: Started; log sequence number 0 43655
Feb 18 02:30:30 ns20984 mysqld[14556]: 090218  2:30:30 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:30:30 ns20984 mysqld[14556]: 090218  2:30:30 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:30:30 ns20984 mysqld[14556]: 090218  2:30:30 [ERROR] Aborting
Feb 18 02:30:30 ns20984 mysqld[14556]: 
Feb 18 02:30:30 ns20984 mysqld[14556]: 090218  2:30:30  InnoDB: Starting shutdown...
Feb 18 02:30:33 ns20984 mysqld[14556]: 090218  2:30:33  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:30:33 ns20984 mysqld[14556]: 090218  2:30:33 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:30:33 ns20984 mysqld[14556]: 
Feb 18 02:30:33 ns20984 mysqld_safe[14568]: ended
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: To do so, start the server, then issue the following commands:
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: Alternatively you can run:
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: /usr/bin/mysql_secure_installation
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: which will also give you the option of removing the test
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: databases and anonymous user created by default.  This is
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: strongly recommended for production servers.
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: See the manual for more instructions.
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: The latest information about MySQL is available on the web at
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: http://www.mysql.com
Feb 18 02:44:59 ns20984 mysqld_safe[14695]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 02:44:59 ns20984 mysqld_safe[14772]: ERROR: 1046  No database selected
Feb 18 02:44:59 ns20984 mysqld_safe[14772]: 090218  2:44:59 [ERROR] Aborting
Feb 18 02:44:59 ns20984 mysqld_safe[14772]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14772]: 090218  2:44:59 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:44:59 ns20984 mysqld_safe[14772]: 
Feb 18 02:44:59 ns20984 mysqld_safe[14899]: started
Feb 18 02:44:59 ns20984 mysqld[14903]: 090218  2:44:59  InnoDB: Started; log sequence number 0 43655
Feb 18 02:44:59 ns20984 mysqld[14903]: 090218  2:44:59 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:44:59 ns20984 mysqld[14903]: 090218  2:44:59 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:44:59 ns20984 mysqld[14903]: 090218  2:44:59 [ERROR] Aborting
Feb 18 02:44:59 ns20984 mysqld[14903]: 
Feb 18 02:44:59 ns20984 mysqld[14903]: 090218  2:44:59  InnoDB: Starting shutdown...
Feb 18 02:45:01 ns20984 mysqld[14903]: 090218  2:45:01  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:45:01 ns20984 mysqld[14903]: 090218  2:45:01 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:45:01 ns20984 mysqld[14903]: 
Feb 18 02:45:01 ns20984 mysqld_safe[14934]: ended
Feb 18 02:45:13 ns20984 /etc/init.d/mysql[15065]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 02:45:13 ns20984 /etc/init.d/mysql[15065]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 02:45:13 ns20984 /etc/init.d/mysql[15065]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 02:45:13 ns20984 /etc/init.d/mysql[15065]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 02:45:13 ns20984 /etc/init.d/mysql[15065]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: To do so, start the server, then issue the following commands:
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: Alternatively you can run:
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: /usr/bin/mysql_secure_installation
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: which will also give you the option of removing the test
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: databases and anonymous user created by default.  This is
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: strongly recommended for production servers.
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: See the manual for more instructions.
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: The latest information about MySQL is available on the web at
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: http://www.mysql.com
Feb 18 02:45:15 ns20984 mysqld_safe[15145]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 02:45:15 ns20984 mysqld_safe[15219]: ERROR: 1046  No database selected
Feb 18 02:45:15 ns20984 mysqld_safe[15219]: 090218  2:45:15 [ERROR] Aborting
Feb 18 02:45:15 ns20984 mysqld_safe[15219]: 
Feb 18 02:45:15 ns20984 mysqld_safe[15219]: 090218  2:45:15 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:45:15 ns20984 mysqld_safe[15219]: 
Feb 18 02:45:16 ns20984 mysqld_safe[15350]: started
Feb 18 02:45:16 ns20984 mysqld[15353]: 090218  2:45:16  InnoDB: Started; log sequence number 0 43655
Feb 18 02:45:16 ns20984 mysqld[15353]: 090218  2:45:16 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 02:45:16 ns20984 mysqld[15353]: 090218  2:45:16 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 02:45:16 ns20984 mysqld[15353]: 090218  2:45:16 [ERROR] Aborting
Feb 18 02:45:16 ns20984 mysqld[15353]: 
Feb 18 02:45:16 ns20984 mysqld[15353]: 090218  2:45:16  InnoDB: Starting shutdown...
Feb 18 02:45:18 ns20984 mysqld[15353]: 090218  2:45:18  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 02:45:18 ns20984 mysqld[15353]: 090218  2:45:18 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 02:45:18 ns20984 mysqld[15353]: 
Feb 18 02:45:18 ns20984 mysqld_safe[15385]: ended
Feb 18 02:45:30 ns20984 /etc/init.d/mysql[15517]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 02:45:30 ns20984 /etc/init.d/mysql[15517]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 02:45:30 ns20984 /etc/init.d/mysql[15517]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 02:45:30 ns20984 /etc/init.d/mysql[15517]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 02:45:30 ns20984 /etc/init.d/mysql[15517]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: To do so, start the server, then issue the following commands:
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: Alternatively you can run:
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: /usr/bin/mysql_secure_installation
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: which will also give you the option of removing the test
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: databases and anonymous user created by default.  This is
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: strongly recommended for production servers.
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: See the manual for more instructions.
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: The latest information about MySQL is available on the web at
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: http://www.mysql.com
Feb 18 03:08:27 ns20984 mysqld_safe[15844]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 03:08:27 ns20984 mysqld_safe[15925]: ERROR: 1046  No database selected
Feb 18 03:08:27 ns20984 mysqld_safe[15925]: 090218  3:08:27 [ERROR] Aborting
Feb 18 03:08:27 ns20984 mysqld_safe[15925]: 
Feb 18 03:08:27 ns20984 mysqld_safe[15925]: 090218  3:08:27 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:08:27 ns20984 mysqld_safe[15925]: 
Feb 18 03:08:27 ns20984 mysqld_safe[16058]: started
Feb 18 03:08:27 ns20984 mysqld[16061]: 090218  3:08:27  InnoDB: Started; log sequence number 0 43655
Feb 18 03:08:27 ns20984 mysqld[16061]: 090218  3:08:27 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 03:08:27 ns20984 mysqld[16061]: 090218  3:08:27 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 03:08:27 ns20984 mysqld[16061]: 090218  3:08:27 [ERROR] Aborting
Feb 18 03:08:27 ns20984 mysqld[16061]: 
Feb 18 03:08:27 ns20984 mysqld[16061]: 090218  3:08:27  InnoDB: Starting shutdown...
Feb 18 03:08:29 ns20984 mysqld[16061]: 090218  3:08:29  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 03:08:29 ns20984 mysqld[16061]: 090218  3:08:29 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:08:29 ns20984 mysqld[16061]: 
Feb 18 03:08:29 ns20984 mysqld_safe[16093]: ended
Feb 18 03:08:41 ns20984 /etc/init.d/mysql[16224]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 03:08:41 ns20984 /etc/init.d/mysql[16224]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 03:08:41 ns20984 /etc/init.d/mysql[16224]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 03:08:41 ns20984 /etc/init.d/mysql[16224]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 03:08:41 ns20984 /etc/init.d/mysql[16224]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: To do so, start the server, then issue the following commands:
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: Alternatively you can run:
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: /usr/bin/mysql_secure_installation
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: which will also give you the option of removing the test
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: databases and anonymous user created by default.  This is
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: strongly recommended for production servers.
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: See the manual for more instructions.
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: The latest information about MySQL is available on the web at
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: http://www.mysql.com
Feb 18 03:11:54 ns20984 mysqld_safe[16379]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 03:11:54 ns20984 mysqld_safe[16456]: ERROR: 1046  No database selected
Feb 18 03:11:54 ns20984 mysqld_safe[16456]: 090218  3:11:54 [ERROR] Aborting
Feb 18 03:11:54 ns20984 mysqld_safe[16456]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16456]: 090218  3:11:54 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:11:54 ns20984 mysqld_safe[16456]: 
Feb 18 03:11:54 ns20984 mysqld_safe[16588]: started
Feb 18 03:11:54 ns20984 mysqld[16591]: 090218  3:11:54  InnoDB: Started; log sequence number 0 43655
Feb 18 03:11:54 ns20984 mysqld[16591]: 090218  3:11:54 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 03:11:54 ns20984 mysqld[16591]: 090218  3:11:54 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 03:11:54 ns20984 mysqld[16591]: 090218  3:11:54 [ERROR] Aborting
Feb 18 03:11:54 ns20984 mysqld[16591]: 
Feb 18 03:11:54 ns20984 mysqld[16591]: 090218  3:11:54  InnoDB: Starting shutdown...
Feb 18 03:11:56 ns20984 mysqld[16591]: 090218  3:11:56  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 03:11:56 ns20984 mysqld[16591]: 090218  3:11:56 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:11:56 ns20984 mysqld[16591]: 
Feb 18 03:11:56 ns20984 mysqld_safe[16623]: ended
Feb 18 03:12:08 ns20984 /etc/init.d/mysql[16754]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 03:12:08 ns20984 /etc/init.d/mysql[16754]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 03:12:08 ns20984 /etc/init.d/mysql[16754]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 03:12:08 ns20984 /etc/init.d/mysql[16754]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 03:12:08 ns20984 /etc/init.d/mysql[16754]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: To do so, start the server, then issue the following commands:
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: Alternatively you can run:
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: /usr/bin/mysql_secure_installation
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: which will also give you the option of removing the test
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: databases and anonymous user created by default.  This is
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: strongly recommended for production servers.
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: See the manual for more instructions.
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: The latest information about MySQL is available on the web at
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: http://www.mysql.com
Feb 18 03:22:07 ns20984 mysqld_safe[17042]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 03:22:07 ns20984 mysqld_safe[17123]: ERROR: 1046  No database selected
Feb 18 03:22:07 ns20984 mysqld_safe[17123]: 090218  3:22:07 [ERROR] Aborting
Feb 18 03:22:07 ns20984 mysqld_safe[17123]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17123]: 090218  3:22:07 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:22:07 ns20984 mysqld_safe[17123]: 
Feb 18 03:22:07 ns20984 mysqld_safe[17257]: started
Feb 18 03:22:07 ns20984 mysqld[17260]: 090218  3:22:07  InnoDB: Started; log sequence number 0 43655
Feb 18 03:22:07 ns20984 mysqld[17260]: 090218  3:22:07 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 03:22:07 ns20984 mysqld[17260]: 090218  3:22:07 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 03:22:07 ns20984 mysqld[17260]: 090218  3:22:07 [ERROR] Aborting
Feb 18 03:22:07 ns20984 mysqld[17260]: 
Feb 18 03:22:07 ns20984 mysqld[17260]: 090218  3:22:07  InnoDB: Starting shutdown...
Feb 18 03:22:09 ns20984 mysqld[17260]: 090218  3:22:09  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 03:22:09 ns20984 mysqld[17260]: 090218  3:22:09 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:22:09 ns20984 mysqld[17260]: 
Feb 18 03:22:09 ns20984 mysqld_safe[17292]: ended
Feb 18 03:22:21 ns20984 /etc/init.d/mysql[17423]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 03:22:21 ns20984 /etc/init.d/mysql[17423]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 03:22:21 ns20984 /etc/init.d/mysql[17423]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 03:22:21 ns20984 /etc/init.d/mysql[17423]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 03:22:21 ns20984 /etc/init.d/mysql[17423]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: To do so, start the server, then issue the following commands:
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: Alternatively you can run:
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: /usr/bin/mysql_secure_installation
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: which will also give you the option of removing the test
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: databases and anonymous user created by default.  This is
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: strongly recommended for production servers.
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: See the manual for more instructions.
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: The latest information about MySQL is available on the web at
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: http://www.mysql.com
Feb 18 03:32:07 ns20984 mysqld_safe[17580]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 03:32:07 ns20984 mysqld_safe[17651]: ERROR: 1046  No database selected
Feb 18 03:32:07 ns20984 mysqld_safe[17651]: 090218  3:32:07 [ERROR] Aborting
Feb 18 03:32:07 ns20984 mysqld_safe[17651]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17651]: 090218  3:32:07 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:32:07 ns20984 mysqld_safe[17651]: 
Feb 18 03:32:07 ns20984 mysqld_safe[17789]: started
Feb 18 03:32:07 ns20984 mysqld[17792]: 090218  3:32:07  InnoDB: Started; log sequence number 0 43655
Feb 18 03:32:07 ns20984 mysqld[17792]: 090218  3:32:07 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 03:32:07 ns20984 mysqld[17792]: 090218  3:32:07 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 03:32:07 ns20984 mysqld[17792]: 090218  3:32:07 [ERROR] Aborting
Feb 18 03:32:07 ns20984 mysqld[17792]: 
Feb 18 03:32:07 ns20984 mysqld[17792]: 090218  3:32:07  InnoDB: Starting shutdown...
Feb 18 03:32:09 ns20984 mysqld[17792]: 090218  3:32:09  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 03:32:09 ns20984 mysqld[17792]: 090218  3:32:09 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 03:32:09 ns20984 mysqld[17792]: 
Feb 18 03:32:09 ns20984 mysqld_safe[17824]: ended
Feb 18 03:32:21 ns20984 /etc/init.d/mysql[17955]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 03:32:21 ns20984 /etc/init.d/mysql[17955]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 03:32:21 ns20984 /etc/init.d/mysql[17955]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 03:32:21 ns20984 /etc/init.d/mysql[17955]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 03:32:21 ns20984 /etc/init.d/mysql[17955]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: To do so, start the server, then issue the following commands:
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: Alternatively you can run:
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: /usr/bin/mysql_secure_installation
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: which will also give you the option of removing the test
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: databases and anonymous user created by default.  This is
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: strongly recommended for production servers.
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: See the manual for more instructions.
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: 
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: The latest information about MySQL is available on the web at
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: http://www.mysql.com
Feb 18 04:20:03 ns20984 mysqld_safe[18310]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 04:20:04 ns20984 mysqld_safe[18388]: ERROR: 1046  No database selected
Feb 18 04:20:04 ns20984 mysqld_safe[18388]: 090218  4:20:04 [ERROR] Aborting
Feb 18 04:20:04 ns20984 mysqld_safe[18388]: 
Feb 18 04:20:04 ns20984 mysqld_safe[18388]: 090218  4:20:04 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:20:04 ns20984 mysqld_safe[18388]: 
Feb 18 04:20:04 ns20984 mysqld_safe[18525]: started
Feb 18 04:20:04 ns20984 mysqld[18528]: 090218  4:20:04  InnoDB: Started; log sequence number 0 43655
Feb 18 04:20:04 ns20984 mysqld[18528]: 090218  4:20:04 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 04:20:04 ns20984 mysqld[18528]: 090218  4:20:04 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 04:20:04 ns20984 mysqld[18528]: 090218  4:20:04 [ERROR] Aborting
Feb 18 04:20:04 ns20984 mysqld[18528]: 
Feb 18 04:20:04 ns20984 mysqld[18528]: 090218  4:20:04  InnoDB: Starting shutdown...
Feb 18 04:20:06 ns20984 mysqld[18528]: 090218  4:20:06  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 04:20:06 ns20984 mysqld[18528]: 090218  4:20:06 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:20:06 ns20984 mysqld[18528]: 
Feb 18 04:20:06 ns20984 mysqld_safe[18562]: ended
Feb 18 04:20:18 ns20984 /etc/init.d/mysql[18693]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 04:20:18 ns20984 /etc/init.d/mysql[18693]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 04:20:18 ns20984 /etc/init.d/mysql[18693]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 04:20:18 ns20984 /etc/init.d/mysql[18693]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 04:20:18 ns20984 /etc/init.d/mysql[18693]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: To do so, start the server, then issue the following commands:
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: Alternatively you can run:
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: /usr/bin/mysql_secure_installation
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: which will also give you the option of removing the test
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: databases and anonymous user created by default.  This is
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: strongly recommended for production servers.
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: See the manual for more instructions.
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: The latest information about MySQL is available on the web at
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: http://www.mysql.com
Feb 18 04:23:04 ns20984 mysqld_safe[18800]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 04:23:04 ns20984 mysqld_safe[18876]: ERROR: 1046  No database selected
Feb 18 04:23:04 ns20984 mysqld_safe[18876]: 090218  4:23:04 [ERROR] Aborting
Feb 18 04:23:04 ns20984 mysqld_safe[18876]: 
Feb 18 04:23:04 ns20984 mysqld_safe[18876]: 090218  4:23:04 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:23:04 ns20984 mysqld_safe[18876]: 
Feb 18 04:23:04 ns20984 mysqld_safe[19011]: started
Feb 18 04:23:04 ns20984 mysqld[19014]: 090218  4:23:04  InnoDB: Started; log sequence number 0 43655
Feb 18 04:23:04 ns20984 mysqld[19014]: 090218  4:23:04 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 04:23:04 ns20984 mysqld[19014]: 090218  4:23:04 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 04:23:04 ns20984 mysqld[19014]: 090218  4:23:04 [ERROR] Aborting
Feb 18 04:23:04 ns20984 mysqld[19014]: 
Feb 18 04:23:04 ns20984 mysqld[19014]: 090218  4:23:04  InnoDB: Starting shutdown...
Feb 18 04:23:06 ns20984 mysqld[19014]: 090218  4:23:06  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 04:23:06 ns20984 mysqld[19014]: 090218  4:23:06 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:23:06 ns20984 mysqld[19014]: 
Feb 18 04:23:06 ns20984 mysqld_safe[19048]: ended
Feb 18 04:23:18 ns20984 /etc/init.d/mysql[19179]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 04:23:18 ns20984 /etc/init.d/mysql[19179]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 04:23:18 ns20984 /etc/init.d/mysql[19179]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 04:23:18 ns20984 /etc/init.d/mysql[19179]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 04:23:18 ns20984 /etc/init.d/mysql[19179]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: To do so, start the server, then issue the following commands:
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: Alternatively you can run:
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: /usr/bin/mysql_secure_installation
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: which will also give you the option of removing the test
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: databases and anonymous user created by default.  This is
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: strongly recommended for production servers.
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: See the manual for more instructions.
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: The latest information about MySQL is available on the web at
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: http://www.mysql.com
Feb 18 04:23:50 ns20984 mysqld_safe[19274]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 04:23:50 ns20984 mysqld_safe[19353]: ERROR: 1046  No database selected
Feb 18 04:23:50 ns20984 mysqld_safe[19353]: 090218  4:23:50 [ERROR] Aborting
Feb 18 04:23:50 ns20984 mysqld_safe[19353]: 
Feb 18 04:23:50 ns20984 mysqld_safe[19353]: 090218  4:23:50 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:23:50 ns20984 mysqld_safe[19353]: 
Feb 18 04:23:51 ns20984 mysqld_safe[19491]: started
Feb 18 04:23:51 ns20984 mysqld[19495]: 090218  4:23:51  InnoDB: Started; log sequence number 0 43655
Feb 18 04:23:51 ns20984 mysqld[19495]: 090218  4:23:51 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 04:23:51 ns20984 mysqld[19495]: 090218  4:23:51 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 04:23:51 ns20984 mysqld[19495]: 090218  4:23:51 [ERROR] Aborting
Feb 18 04:23:51 ns20984 mysqld[19495]: 
Feb 18 04:23:51 ns20984 mysqld[19495]: 090218  4:23:51  InnoDB: Starting shutdown...
Feb 18 04:23:53 ns20984 mysqld[19495]: 090218  4:23:53  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 04:23:53 ns20984 mysqld[19495]: 090218  4:23:53 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 04:23:53 ns20984 mysqld[19495]: 
Feb 18 04:23:53 ns20984 mysqld_safe[19528]: ended
Feb 18 04:24:05 ns20984 /etc/init.d/mysql[19659]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 04:24:05 ns20984 /etc/init.d/mysql[19659]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 04:24:05 ns20984 /etc/init.d/mysql[19659]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 04:24:05 ns20984 /etc/init.d/mysql[19659]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 04:24:05 ns20984 /etc/init.d/mysql[19659]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: To do so, start the server, then issue the following commands:
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: /usr/bin/mysqladmin -u root password 'new-password'
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: /usr/bin/mysqladmin -u root -h ns20984.ovh.net password 'new-password'
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: Alternatively you can run:
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: /usr/bin/mysql_secure_installation
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: which will also give you the option of removing the test
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: databases and anonymous user created by default.  This is
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: strongly recommended for production servers.
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: See the manual for more instructions.
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: Please report any problems with the /usr/bin/mysqlbug script!
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: The latest information about MySQL is available on the web at
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: http://www.mysql.com
Feb 18 05:14:53 ns20984 mysqld_safe[21730]: Support MySQL by buying support/licenses at http://shop.mysql.com
Feb 18 05:14:53 ns20984 mysqld_safe[21805]: ERROR: 1046  No database selected
Feb 18 05:14:53 ns20984 mysqld_safe[21805]: 090218  5:14:53 [ERROR] Aborting
Feb 18 05:14:53 ns20984 mysqld_safe[21805]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21805]: 090218  5:14:53 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 05:14:53 ns20984 mysqld_safe[21805]: 
Feb 18 05:14:53 ns20984 mysqld_safe[21932]: started
Feb 18 05:14:54 ns20984 mysqld[21935]: 090218  5:14:54  InnoDB: Started; log sequence number 0 43655
Feb 18 05:14:54 ns20984 mysqld[21935]: 090218  5:14:54 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 05:14:54 ns20984 mysqld[21935]: 090218  5:14:54 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 05:14:54 ns20984 mysqld[21935]: 090218  5:14:54 [ERROR] Aborting
Feb 18 05:14:54 ns20984 mysqld[21935]: 
Feb 18 05:14:54 ns20984 mysqld[21935]: 090218  5:14:54  InnoDB: Starting shutdown...
Feb 18 05:14:56 ns20984 mysqld[21935]: 090218  5:14:56  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 05:14:56 ns20984 mysqld[21935]: 090218  5:14:56 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 05:14:56 ns20984 mysqld[21935]: 
Feb 18 05:14:56 ns20984 mysqld_safe[21967]: ended
Feb 18 05:15:08 ns20984 /etc/init.d/mysql[22100]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 05:15:08 ns20984 /etc/init.d/mysql[22100]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 05:15:08 ns20984 /etc/init.d/mysql[22100]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 05:15:08 ns20984 /etc/init.d/mysql[22100]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 05:15:08 ns20984 /etc/init.d/mysql[22100]: 
Feb 18 05:27:23 ns20984 mysqld_safe[22454]: started
Feb 18 05:27:23 ns20984 mysqld[22457]: 090218  5:27:23  InnoDB: Started; log sequence number 0 43655
Feb 18 05:27:23 ns20984 mysqld[22457]: 090218  5:27:23 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
Feb 18 05:27:23 ns20984 mysqld[22457]: 090218  5:27:23 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Feb 18 05:27:23 ns20984 mysqld[22457]: 090218  5:27:23 [ERROR] Aborting
Feb 18 05:27:23 ns20984 mysqld[22457]: 
Feb 18 05:27:23 ns20984 mysqld[22457]: 090218  5:27:23  InnoDB: Starting shutdown...
Feb 18 05:27:25 ns20984 mysqld[22457]: 090218  5:27:25  InnoDB: Shutdown completed; log sequence number 0 43655
Feb 18 05:27:25 ns20984 mysqld[22457]: 090218  5:27:25 [Note] /usr/sbin/mysqld: Shutdown complete
Feb 18 05:27:25 ns20984 mysqld[22457]: 
Feb 18 05:27:25 ns20984 mysqld_safe[22490]: ended
Feb 18 05:27:37 ns20984 /etc/init.d/mysql[22623]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Feb 18 05:27:37 ns20984 /etc/init.d/mysql[22623]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Feb 18 05:27:37 ns20984 /etc/init.d/mysql[22623]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Feb 18 05:27:37 ns20984 /etc/init.d/mysql[22623]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Feb 18 05:27:37 ns20984 /etc/init.d/mysql[22623]: 
root@ns20984:~# 

```


Preconfiguring packages ...
Selecting previously deselected package libmcrypt4.
(Reading database ... 123193 files and directories currently installed.)
Unpacking libmcrypt4 (from .../libmcrypt4_2.5.7-5_i386.deb) ...
Selecting previously deselected package php5-mcrypt.
Unpacking php5-mcrypt (from .../php5-mcrypt_5.2.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package phpmyadmin.
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.11.3-1ubuntu1.1_all.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld
   ...done.
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
FATAL: Could not load /lib/modules/2.6.28.1-xxxx-std-ipv4-32/modules.dep: No such file or directory
Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Setting up libmcrypt4 (2.5.7-5) ...

Setting up php5-mcrypt (5.2.3-0ubuntu1) ...

Setting up phpmyadmin (4:2.11.3-1ubuntu1.1) ...
Syntax error on line 1 of /etc/apache2/conf.d/fqdn.save:
Invalid command 'G', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
invoke-rc.d: initscript apache2, action "reload" failed.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
 * Stopping MySQL database server mysqld
   ...done.
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
grep: /proc/modules: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
FATAL: Could not load /lib/modules/2.6.28.1-xxxx-std-ipv4-32/modules.dep: No such file or directory
Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting MySQL database server mysqld
   ...fail!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured

---

