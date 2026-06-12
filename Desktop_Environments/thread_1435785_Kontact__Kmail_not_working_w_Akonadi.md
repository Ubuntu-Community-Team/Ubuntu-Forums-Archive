---
title: "Kontact / Kmail not working w/ Akonadi"
date: 2010-03-21
forum: Desktop Environments
---

### Post by bluedalek on 2010-03-21
Hey all

I just upgraded to 10.04LTS and so far, so good! Every thing is running smoothly, except my email clients.  Neither Kontact or Kmail will start up.  This Akonadi Server thing keeps giving me an error.  this is the report that I get when it fails to run:

```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/gentle/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
SizeThreshold=4096
ExternalPayload=false

[QMYSQL]
Name=akonadi
Host=
User=
Password=
Options="UNIX_SOCKET=/home/gentle/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true


Test 2:  SUCCESS
--------

MySQL server found.
Details: You currently have configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld', its locations varies depending on the distribution.

Test 3:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.41-3ubuntu4 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 4:  SUCCESS
--------

No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup into '/home/gentle/.local/share/akonadi/db_data/mysql.err'.

Test 5:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href='/etc/akonadi/mysql-global.conf'>/etc/akonadi/mysql-global.conf</a>.

File content of '/etc/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=latin1
collation_server=latin1_general_ci
table_cache=200
thread_cache_size=3
log_bin=mysql-bin
expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2



Test 6:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 7:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/gentle/.local/share/akonadi/mysql.conf'>/home/gentle/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/gentle/.local/share/akonadi/mysql.conf':


Test 8:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.3.1


Test 9:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 10:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  SUCCESS
--------

Nepomuk search service registered at D-Bus.
Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational.

Test 12:  SUCCESS
--------

Nepomuk search service uses an appropriate backend. 
Details: The Nepomuk search service uses one of the recommended backends.

Test 13:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 14:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 15:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/home/gentle/.local/share/akonadi/akonadiserver.error'>/home/gentle/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/gentle/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/gentle/.local/share/akonadi//mysql.conf", "--datadir=/home/gentle/.local/share/akonadi/db_data/", "--socket=/home/gentle/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "100321 22:23:15 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Table 'mysql.plugin' doesn't exist
100321 22:23:15 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
InnoDB: Error: log file ./ib_logfile0 is of different size 0 67108864 bytes
InnoDB: than specified in the .cnf file 0 5242880 bytes!
100321 22:23:15 [ERROR] Plugin 'InnoDB' init function returned error.
100321 22:23:15 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
100321 22:23:15 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b489]
1: akonadiserver() [0x40b9d2]
2: /lib/libc.so.6(+0x33b00) [0x7f0d372c7b00]
3: /lib/libc.so.6(gsignal+0x35) [0x7f0d372c7a85]
4: /lib/libc.so.6(abort+0x180) [0x7f0d372cb520]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f0d384ac844]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40cad8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f0d3853b3b7]
8: /usr/lib/libQtCore.so.4(+0x1124c9) [0x7f0d3854d4c9]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f0d3854e6c9]
10: akonadiserver(_ZN6QDebugD1Ev+0x4e) [0x406fde]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer25startMysqlDatabaseProcessEv+0x183b) [0x7f0d3891c07b]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x2e0) [0x7f0d38920b50]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x76) [0x7f0d38920e16]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f0d3892213a]
15: akonadiserver(main+0x3b7) [0x406617]
16: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f0d372b2c4d]
17: akonadiserver() [0x406169]
]
" 


Test 16:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/home/gentle/.local/share/akonadi/akonadiserver.error.old'>/home/gentle/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/gentle/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/gentle/.local/share/akonadi//mysql.conf", "--datadir=/home/gentle/.local/share/akonadi/db_data/", "--socket=/home/gentle/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "100321 22:23:15 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Table 'mysql.plugin' doesn't exist
100321 22:23:15 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
InnoDB: Error: log file ./ib_logfile0 is of different size 0 67108864 bytes
InnoDB: than specified in the .cnf file 0 5242880 bytes!
100321 22:23:15 [ERROR] Plugin 'InnoDB' init function returned error.
100321 22:23:15 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
100321 22:23:15 [ERROR] Fatal error: Can't open and lock privilege tables: Table 'mysql.host' doesn't exist
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40b489]
1: akonadiserver() [0x40b9d2]
2: /lib/libc.so.6(+0x33b00) [0x7f05841f9b00]
3: /lib/libc.so.6(gsignal+0x35) [0x7f05841f9a85]
4: /lib/libc.so.6(abort+0x180) [0x7f05841fd520]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f05853de844]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40cad8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f058546d3b7]
8: /usr/lib/libQtCore.so.4(+0x1124c9) [0x7f058547f4c9]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f05854806c9]
10: akonadiserver(_ZN6QDebugD1Ev+0x4e) [0x406fde]
11: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer25startMysqlDatabaseProcessEv+0x183b) [0x7f058584e07b]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x2e0) [0x7f0585852b50]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x76) [0x7f0585852e16]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f058585413a]
15: akonadiserver(main+0x3b7) [0x406617]
16: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f05841e4c4d]
17: akonadiserver() [0x406169]
]
" 


Test 17:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 18:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```

If anyone has any thoughts how to resolve this, it would be greatly appreciated!

---

### Post by Chame_Wizard on 2010-03-22
I think you have to installing a dependency.

---

### Post by darrenm on 2010-03-28
I just installed anything I could find with akonadi in the name and it's started working.

---

### Post by ZeDeun on 2010-06-10
Hi,

Yes you are riçght it was a question of dependencies : I had installed  everything except the ones with ruby, transitional and development.
It works now. Thanks. :p

---

