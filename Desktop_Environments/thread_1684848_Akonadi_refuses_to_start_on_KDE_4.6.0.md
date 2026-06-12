---
title: "Akonadi refuses to start on KDE 4.6.0"
date: 2011-02-09
forum: Desktop Environments
---

### Post by PatchesTheCaveman on 2011-02-09
Akonadi refuses to start on KDE 4.6.0 installed from the *kubuntu-backports* PPA on Ubuntu 10.10 Maverick Meerkat, preventing me from using KMail.  Here is the full error output:
```
patches@pleistocene:~/.local/share$ akonadictl start
Starting Akonadi Server...
   done.
patches@pleistocene:~/.local/share$ Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
search paths:  ("/home/patches/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Found mysql_install_db:  "/usr/bin/mysql_install_db" 
Found mysqlcheck:  "/usr/bin/mysqlcheck" 
Database process exited unexpectedly during initial connection!
executable: "/usr/sbin/mysqld-akonadi"
arguments: ("--defaults-file=/home/patches/.local/share/akonadi//mysql.conf", "--datadir=/home/patches/.local/share/akonadi/db_data/", "--socket=/home/patches/.local/share/akonadi/socket-pleistocene/mysql.socket")
stdout: ""
stderr: "Could not open required defaults file: /home/patches/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
110209 16:41:12 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110209 16:41:12  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8086055]
1: akonadiserver() [0x8086516]
2: [0xb772e400]
3: [0xb772e416]
4: /lib/libc.so.6(gsignal+0x51) [0xb6e9f941]
5: /lib/libc.so.6(abort+0x182) [0xb6ea2e42]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xb74d62dc]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8087574]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x8e) [0xb757168e]
9: /usr/lib/libQtCore.so.4(+0x103425) [0xb7581425]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3d) [0xb758295d]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x8081b73]
12: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1c27) [0x810c177]
13: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8087a23]
14: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xca) [0x8088b6a]
15: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x48) [0x808a1d8]
16: akonadiserver(main+0x364) [0x8080fb4]
17: /lib/libc.so.6(__libc_start_main+0xe7) [0xb6e8bce7]
18: akonadiserver() [0x8080b81]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/home/patches/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Found mysql_install_db:  "/usr/bin/mysql_install_db" 
Found mysqlcheck:  "/usr/bin/mysqlcheck" 
Database process exited unexpectedly during initial connection!
executable: "/usr/sbin/mysqld-akonadi"
arguments: ("--defaults-file=/home/patches/.local/share/akonadi//mysql.conf", "--datadir=/home/patches/.local/share/akonadi/db_data/", "--socket=/home/patches/.local/share/akonadi/socket-pleistocene/mysql.socket")
stdout: ""
stderr: "Could not open required defaults file: /home/patches/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
110209 16:41:12 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110209 16:41:12  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8086055]
1: akonadiserver() [0x8086516]
2: [0xb77ae400]
3: [0xb77ae416]
4: /lib/libc.so.6(gsignal+0x51) [0xb6f1f941]
5: /lib/libc.so.6(abort+0x182) [0xb6f22e42]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xb75562dc]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8087574]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x8e) [0xb75f168e]
9: /usr/lib/libQtCore.so.4(+0x103425) [0xb7601425]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3d) [0xb760295d]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x8081b73]
12: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1c27) [0x810c177]
13: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8087a23]
14: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xca) [0x8088b6a]
15: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x48) [0x808a1d8]
16: akonadiserver(main+0x364) [0x8080fb4]
17: /lib/libc.so.6(__libc_start_main+0xe7) [0xb6f0bce7]
18: akonadiserver() [0x8080b81]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/home/patches/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Found mysql_install_db:  "/usr/bin/mysql_install_db" 
Found mysqlcheck:  "/usr/bin/mysqlcheck" 
Database process exited unexpectedly during initial connection!
executable: "/usr/sbin/mysqld-akonadi"
arguments: ("--defaults-file=/home/patches/.local/share/akonadi//mysql.conf", "--datadir=/home/patches/.local/share/akonadi/db_data/", "--socket=/home/patches/.local/share/akonadi/socket-pleistocene/mysql.socket")
stdout: ""
stderr: "Could not open required defaults file: /home/patches/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
110209 16:41:12 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110209 16:41:12  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8086055]
1: akonadiserver() [0x8086516]
2: [0xb778b400]
3: [0xb778b416]
4: /lib/libc.so.6(gsignal+0x51) [0xb6efc941]
5: /lib/libc.so.6(abort+0x182) [0xb6effe42]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xb75332dc]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8087574]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x8e) [0xb75ce68e]
9: /usr/lib/libQtCore.so.4(+0x103425) [0xb75de425]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3d) [0xb75df95d]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x8081b73]
12: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1c27) [0x810c177]
13: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8087a23]
14: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xca) [0x8088b6a]
15: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x48) [0x808a1d8]
16: akonadiserver(main+0x364) [0x8080fb4]
17: /lib/libc.so.6(__libc_start_main+0xe7) [0xb6ee8ce7]
18: akonadiserver() [0x8080b81]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
search paths:  ("/home/patches/bin", "/usr/local/sbin", "/usr/local/bin", "/usr/sbin", "/usr/bin", "/sbin", "/bin", "/usr/games", "/usr/sbin", "/usr/local/sbin", "/usr/local/libexec", "/usr/libexec", "/opt/mysql/libexec", "/opt/local/lib/mysql5/bin", "/opt/mysql/sbin") 
Found mysql_install_db:  "/usr/bin/mysql_install_db" 
Found mysqlcheck:  "/usr/bin/mysqlcheck" 
Database process exited unexpectedly during initial connection!
executable: "/usr/sbin/mysqld-akonadi"
arguments: ("--defaults-file=/home/patches/.local/share/akonadi//mysql.conf", "--datadir=/home/patches/.local/share/akonadi/db_data/", "--socket=/home/patches/.local/share/akonadi/socket-pleistocene/mysql.socket")
stdout: ""
stderr: "Could not open required defaults file: /home/patches/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Warning] Can't create test file /home/patches/.local/share/akonadi/db_data/pleistocene.lower-test
110209 16:41:12 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Can't find file: './mysql/plugin.frm' (errno: 13)
110209 16:41:12 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
110209 16:41:12  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x35) [0x8086055]
1: akonadiserver() [0x8086516]
2: [0xb784e400]
3: [0xb784e416]
4: /lib/libc.so.6(gsignal+0x51) [0xb6fbf941]
5: /lib/libc.so.6(abort+0x182) [0xb6fc2e42]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x8c) [0xb75f62dc]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8087574]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x8e) [0xb769168e]
9: /usr/lib/libQtCore.so.4(+0x103425) [0xb76a1425]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3d) [0xb76a295d]
11: akonadiserver(_ZN6QDebugD1Ev+0x43) [0x8081b73]
12: akonadiserver(_ZN13DbConfigMysql19startInternalServerEv+0x1c27) [0x810c177]
13: akonadiserver(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xe3) [0x8087a23]
14: akonadiserver(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xca) [0x8088b6a]
15: akonadiserver(_ZN7Akonadi13AkonadiServer8instanceEv+0x48) [0x808a1d8]
16: akonadiserver(main+0x364) [0x8080fb4]
17: /lib/libc.so.6(__libc_start_main+0xe7) [0xb6fabce7]
18: akonadiserver() [0x8080b81]
]
"
ProcessControl: Application 'akonadiserver' returned with exit code 255 (Unknown error)
"akonadiserver" crashed too often and will not be restarted!
```

I've tried moving the ~/.local/share/akonadi directory to give it a fresh start, and even trying it from a brand new user account, all to no avail.

---

### Post by jamadagni on 2011-06-18
Hello. See [https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/707464](https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/707464) and [https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/578357](https://bugs.launchpad.net/ubuntu/+source/akonadi/+bug/578357). I have made a note there of the fix that worked for me. HTH. Thanks.

---

