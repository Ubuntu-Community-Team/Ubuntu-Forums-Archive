---
title: "Akonadi pains"
date: 2010-03-08
forum: Desktop Environments
---

### Post by voidzero on 2010-03-08
Hi,

After upgrading from jaunty to karmic, kresmigrator shows up for a brief amount of time, showing errors about akonadi. I have tried to capture the error. I don't need akonadi, never used it, and want to get rid of the error. I have searched the forums but can't find any solution. Also, it complains about dbus but I couldn't capture that error.


```
No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

```

And

```
Database process exited unexpectedly during initial connection!
executable: "/usr/sbin/mysqld-akonadi"
arguments: ("--defaults-file=/home/void/.local/share/akonadi//mysql.conf", "--datadir=/home/void/.local/share/akonadi/db_data/", "--socket=/home/void/.local/share/akonadi/db_misc/mysql.socket")
stdout: ""
stderr: "Could not open required defaults file: /home/void/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
100308 11:41:36 [Warning] Can't create test file /home/void/.local/share/akonadi/db_data/athena.lower-test
100308 11:41:36 [Warning] Can't create test file /home/void/.local/share/akonadi/db_data/athena.lower-test
100308 11:41:36 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Table 'mysql.plugin' doesn't exist
100308 11:41:36 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
100308 11:41:36  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
"
exit code: 1
process error: "Unknown error"
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b1a9]
1: akonadiserver [0x40b6f2]
2: /lib/libc.so.6 [0x7ff445473530]
3: /lib/libc.so.6(gsignal+0x35) [0x7ff4454734b5]
4: /lib/libc.so.6(abort+0x180) [0x7ff445476f50]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7ff446402864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c2a8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x6e) [0x7ff44648db5e]
8: /usr/lib/libQtCore.so.4 [0x7ff44649b909]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0x7ff44649c938]
10: akonadiserver(_ZN6QDebugD1Ev+0x45) [0x406dc5]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x18bd) [0x7ff446a523fd]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x69) [0x7ff446a545f9]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7ff446a5582a]
14: akonadiserver(main+0x3f1) [0x4062d1]
15: /lib/libc.so.6(__libc_start_main+0xfd) [0x7ff44545eabd]
16: akonadiserver [0x405de9]
]
"

```

How can I get rid of this stuff?

---

### Post by voidzero on 2010-03-10
Found it! Posting the solution here for archiving purposes.

```
sudo aa-complain mysqld
sudo aa-complain mysqld-akonadi
sudo /etc/init.d/apparmor reload
```

\\:D/

---

