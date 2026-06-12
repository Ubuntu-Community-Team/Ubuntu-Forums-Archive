---
title: "Akonadi blocks kmail"
date: 2010-10-13
forum: Desktop Environments
---

### Post by dargaud on 2010-10-13
Hello all,
I did a clean install of Kubuntu 10.10 yesterday. Everything worked perfect... except kmail. Two things that are relevant:
- I kept my old /home
- I installed mysql server
When I launch kmail I see it get started, it download mails, I can click on messages, but after a few seconds I get an error popup: **Akonadi Server Self-Test - Kmail** and it fails.

Here's the full report:
```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/dargaud/.config/akonadi/akonadiserverrc':
[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/home/dargaud/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true


Test 2:  SUCCESS
--------

Akonadi is not running as root
Details: Akonadi is not running as a root/administrator user, which is the recommended setup for a secure system.

Test 3:  SUCCESS
--------

MySQL server found.
Details: You have currently configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld'; its location varies depending on the distribution.

Test 4:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.48-1ubuntu4 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 5:  SUCCESS
--------

No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup. The log can be found in '/home/dargaud/.local/share/akonadi/db_data/mysql.err'.

Test 6:  SUCCESS
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
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
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

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/dargaud/.local/share/akonadi/mysql.conf'>/home/dargaud/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/dargaud/.local/share/akonadi/mysql.conf':
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
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
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

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.4.0


Test 10:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  ERROR
--------

Nepomuk search service not registered at D-Bus.
Details: The Nepomuk search service is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 13:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 14:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents /usr/local/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share'; make sure this includes all paths where Akonadi agents are installed.

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
Directory listing of '/usr/local/share/akonadi/agents':
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
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href='/home/dargaud/.local/share/akonadi/akonadiserver.error'>/home/dargaud/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/dargaud/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/dargaud/.local/share/akonadi//mysql.conf", "--datadir", "/home/dargaud/.local/share/akonadi/db_data/", "--socket=/home/dargaud/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /home/dargaud/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
101013 18:59:04 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
101013 18:59:04 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
101013 18:59:04 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Table 'mysql.plugin' doesn't exist
101013 18:59:04 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101013 18:59:04  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40af99]
1: akonadiserver() [0x40b4ea]
2: /lib/libc.so.6(+0x33c20) [0x7ff1cd52fc20]
3: /lib/libc.so.6(gsignal+0x35) [0x7ff1cd52fba5]
4: /lib/libc.so.6(abort+0x180) [0x7ff1cd5336b0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7ff1ce712864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c5d8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7ff1ce7a44a7]
8: /usr/lib/libQtCore.so.4(+0x10ba59) [0x7ff1ce7b1a59]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7ff1ce7b2c69]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4068f9]
11: /usr/lib/libakonadiprivate.so.1(_ZN13DbConfigMysql19startInternalServerEv+0x19ad) [0x7ff1cec346ad]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xdd) [0x7ff1ceb9e8cd]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xd7) [0x7ff1ceba07e7]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7ff1ceba21ea]
15: akonadiserver(main+0x404) [0x405df4]
16: /lib/libc.so.6(__libc_start_main+0xfe) [0x7ff1cd51ad8e]
17: akonadiserver() [0x4058f9]
]
" 


Test 16:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/home/dargaud/.local/share/akonadi/akonadiserver.error.old'>/home/dargaud/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/dargaud/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/dargaud/.local/share/akonadi//mysql.conf", "--datadir", "/home/dargaud/.local/share/akonadi/db_data/", "--socket=/home/dargaud/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /home/dargaud/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
101013 18:59:04 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
101013 18:59:04 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
101013 18:59:04 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld-akonadi: Table 'mysql.plugin' doesn't exist
101013 18:59:04 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
101013 18:59:04  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver(_Z11akBacktracev+0x39) [0x40af99]
1: akonadiserver() [0x40b4ea]
2: /lib/libc.so.6(+0x33c20) [0x7f630c6a0c20]
3: /lib/libc.so.6(gsignal+0x35) [0x7f630c6a0ba5]
4: /lib/libc.so.6(abort+0x180) [0x7f630c6a46b0]
5: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x74) [0x7f630d883864]
6: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xa8) [0x40c5d8]
7: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x77) [0x7f630d9154a7]
8: /usr/lib/libQtCore.so.4(+0x10ba59) [0x7f630d922a59]
9: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f630d923c69]
10: akonadiserver(_ZN6QDebugD1Ev+0x49) [0x4068f9]
11: /usr/lib/libakonadiprivate.so.1(_ZN13DbConfigMysql19startInternalServerEv+0x19ad) [0x7f630dda56ad]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0xdd) [0x7f630dd0f8cd]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0xd7) [0x7f630dd117e7]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x4a) [0x7f630dd131ea]
15: akonadiserver(main+0x404) [0x405df4]
16: /lib/libc.so.6(__libc_start_main+0xfe) [0x7f630c68bd8e]
17: akonadiserver() [0x4058f9]
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

I've tried to follow the indications found [here]("http://userbase.kde.org/Akonadi_4.4/Troubleshooting") :
```
kcmshell4 kcm_akonadi
```
Trying the internal MySql or my own, but it doesn't change anything.

I don't care about Akonadi, but when I went to apt-get remove it, it wanted to take away 60 rather crucial packages with it...

I've delete everything related to akonadi I could find, but it didn't change a thing:
```
rm -rf .local/share/akonadi .config/akonadi .kde/share/config/akonadi-firstrunrc

```

---

### Post by dargaud on 2010-10-13
Sorry folks, 10 seconds after posting this, I dropped the database and akonadi rebuilt it. Works fine now.

---

### Post by liste on 2010-11-03
Hello, dargaud!

Would you mind explaining which database you dropped and how you did it, please?  I am having a similar problem on Ubuntu, and posted my problem here: [http://art.ubuntuforums.org/showthread.php?t=1612747](http://art.ubuntuforums.org/showthread.php?t=1612747)

I don't know if the problem is similar or not, or whether dropping a database and rebuilding it would work.  If you have any suggestions, I would be extremely grateful!

Thank you!

---

### Post by dargaud on 2010-11-08
IIRC I used phpmyadmin, root login and did a 'drop database' on akonadi.

---

### Post by liste on 2010-11-08
Thank you, dargaud!

I finally discovered that I had to install kde-systemsettings from Ubuntu Software Centre.  From there I was able to get hold of some configuration files.  The only thing I'm lacking now is the distribution lists.  They are there in my kAddressBook, but unavailable in my "distribution list" from my kMail.  :(

If you have any suggestions, I'd be extremely grateful!

Again, thank you for your fast response!

---

### Post by kirijin on 2011-01-15
Hello! 

The same problem here. Could you please give copy/paste commands for terminal to make it easier?

Thanks beforehand!

---

### Post by dargaud on 2011-01-17
If you don't know phpmyadmin and/or sql, it's not something that can be easily explained (sorry, I'm not trying to be haughty here). I don't think the authors of akonadi ever planed for manual intervention like I did, or if they did they certainly didn't leave tools around... If mysql is not installed, I don't know what akonadi relies on.

---

### Post by Xristoph on 2011-03-28
Not sure if this is a general solution but for me it works. Yesterday i figured that Kmail freezes. Gooogling brought up all the tips about restarting akonadi, checking that the mysql server is running etc. Finally i figured that  mysql_upgrade had the problem that it always was started (i do not have any idea by who) as
/usr/bin/mysql_upgrade 
instead of 
/usr/bin/mysql_upgrade --defaults-extra-file=/etc/mysql/debian.cnf

finally beeing already quite tired and desperate i did the following

sudo ln -s /etc/mysql/debian.cnf to /etc/mysql/conf.d/debian.cnf

I have to admit before i also explicitly added the user listed in /etc/mysql/debian.cnf to the users table of mysql, eventhough meanwhile i do think, that this was not necessary at all. 

As it already was late and the link didn't seem to work, I switched the computer off and went to bed.
Back from work today i fired up the system and had already, when starting kontact, the subjective impression, that everything is a bit faster. And voila, when trying to sent a test message to my office mail account, kmail came up with the password request for the smtp server just in not time. Usually  it took minutes. And the best no freeze till now. 

Christoph

---

### Post by Xristoph on 2011-03-29
Again me. It works as long as the akonadi server is started by root, best along with KDM. If it is not started do not start it as user but as root by

sudo akonadictl start

and when you need to restart use

sudo akonadictl restart

any thing else will not work as the startup will fail in mysqlchek not being able to login as root. 

Xristoph

---

### Post by dargaud on 2013-04-23
I don't like the idea of starting akonadi as root because it stores its files in your home directory. It means that some files in your home will now be owned by root, which means that you won't be able to do a /home backup as yourself but need elevated priviledges (or do a chown -R ~ beforehand) and all kind of weird consequences.

---

### Post by wildmanne39 on 2013-04-23
Thread closed. Please do not post in old threads.

---

