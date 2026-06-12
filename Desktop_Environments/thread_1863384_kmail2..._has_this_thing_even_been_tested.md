---
title: "kmail2... has this thing even been tested ?"
date: 2011-10-17
forum: Desktop Environments
---

### Post by dargaud on 2011-10-17
Hello all,
OK, I did the do-release-upgrade on kubuntu and everything seems to have gone well. Except for kmail. First it told me it needed to migrate my mail, failed, I had to do it manually and also update them after migrating. OK, so now all my 20+ years of messages are here, new messages come in fine after some farts with the wallet, but:
[LIST]
[*]I can't delete messages: "kmail folders: cannot modify emails in folder". Actually they disappear, but I still get the message for every deletion.
[*]I can't send messages, they just sit in the outbox and when I try "Send Queued messages" I get: *kmail2(23168)/kdepimlibs (mailtransport) MailTransport::SendQueuedAction::itemAccepted: Item doesn't have DispatchModeAttribute*. Not very helpful. 

[/LIST]
I searched for those issues without success.

---

### Post by dargaud on 2011-10-18
And it gets worse... Following some indications on the net, I installed akonadiconsole and removed/reinstated the mail dispatch agent. After that I could not move or delete any email from my store. I tried to remove ~/.kde/share/apps/kmai and kmail2 (I have a backup), but when I restart kmail, I still see all the messages, and I still can't move/delete them. Are they cached somehow (I'm on POP3).

How can I reset kmail2 to a pristine state and reimport from scratch ?!?

---

### Post by pwabrahams on 2011-10-19
I too am a kmail2 victim.  I did the migration from kmail and found that the messages in one of my inboxes couldn't be deleted -- "Move to Trash" was greyed out, and there seemed to be some permissions problem.  My attempts to fix the problem only made matters worse - *much* worse.  I thought that the existence of "Local Folders" among the accounts was a mistake, so I deleted it.  Wrong move!  When I did that, all my email vanished.  (Not quite; the files are still there, but in structures that I don't know how to reconnect to kmail.)  At this point the messages in my (new) outbox can't be sent; "Send queued messages" does nothing.  And the software environment, involving akonadi, is quite opaque, making everything very difficult to fix.

---

### Post by Orval on 2011-10-21
Today I couldn't send any emails. Annoying, because I need to send emails for work.

---

### Post by dargaud on 2011-10-21
Yeah, I've been pretty good at making it much worse too. Now kmail takes a long time to start, it's completely empty (no inbox, thrash...) and it gives me error messages on my various accounts: ```
mailinglists: Error while trying to get the local inbox folder, aborting mail check.
Cannot connect to the Akonadi service. (Agent instance creation timed out.
```
I've tried reinstalling kmail to no avail. I even declared a new user and logged anew, but kmail complains that akonadi won't start. I have my backup, but what can I do with it, short of reinstalling the OS (which I'd rather avoid on that machine that has tons of servers running).

---

### Post by dargaud on 2011-10-23
OK. I gave up and reinstalled 11.10 from scratch on my main drive (I kept a tarfile of /, but no image backup, so I can't turn back). I boot into my new account (I haven't copied anything from my old account) and launch kmail. And guess what: ```
The Akonadi personal information management service is not operational
```. Come on ! On a fresh install you can't even launch the mail program ?!? What. The. ****. Seriously.
```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/dargaud/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL

[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/home/dargaud/.local/share/akonadi/socket-penguin/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true

[Debug]
Tracer=null


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
Details: MySQL server found: /usr/sbin/mysqld  Ver 5.1.58-1ubuntu1 for debian-linux-gnu on x86_64 ((Ubuntu))


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
wait_timeout=31536000

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
wait_timeout=31536000

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.6.2


Test 10:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  SUCCESS
--------

Nepomuk search service registered at D-Bus.
Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational.

Test 13:  SUCCESS
--------

Nepomuk search service uses an appropriate backend. 
Details: The Nepomuk search service uses one of the recommended backends.

Test 14:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 15:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share/default:/usr/local/share/:/usr/share/'; make sure this includes all paths where Akonadi agents are installed.

Directory listing of '/usr/share/akonadi/agents':
akonotesresource.desktop
birthdaysresource.desktop
calendarsearchagent.desktop
contactsresource.desktop
davgroupwareresource.desktop
icalresource.desktop
imapresource.desktop
invitationsagent.desktop
kabcresource.desktop
kcalresource.desktop
kdeaccountsresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mixedmaildirresource.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share/default:/usr/local/share/:/usr/share/'

Test 16:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href='/home/dargaud/.local/share/akonadi/akonadiserver.error'>/home/dargaud/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/dargaud/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/dargaud/.local/share/akonadi//mysql.conf", "--datadir=/home/dargaud/.local/share/akonadi/db_data/", "--socket=/home/dargaud/.local/share/akonadi/socket-penguin/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /home/dargaud/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
111023 18:58:29 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
111023 18:58:29 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
111023 18:58:29 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
111023 18:58:29 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
111023 18:58:29  InnoDB: Initializing buffer pool, size = 8.0M
111023 18:58:29  InnoDB: Completed initialization of buffer pool
111023 18:58:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x4168d4]
1: akonadiserver() [0x416c6c]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x36420) [0x7f55deb9f420]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35) [0x7f55deb9f3a5]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x17b) [0x7f55deba2b0b]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x11b) [0x7f55e086d43b]
6: akonadiserver() [0x4182e2]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xaf) [0x7f55e08fb1ff]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x112943) [0x7f55e0903943]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f55e090c7c9]
10: akonadiserver() [0x4124e6]
11: akonadiserver() [0x49a9d3]
12: akonadiserver() [0x418762]
13: akonadiserver() [0x419f2c]
14: akonadiserver() [0x41b567]
15: akonadiserver() [0x411ae2]
16: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f55deb8a30d]
17: akonadiserver() [0x412371]
]
" 


Test 17:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/home/dargaud/.local/share/akonadi/akonadiserver.error.old'>/home/dargaud/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/dargaud/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/dargaud/.local/share/akonadi//mysql.conf", "--datadir=/home/dargaud/.local/share/akonadi/db_data/", "--socket=/home/dargaud/.local/share/akonadi/socket-penguin/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /home/dargaud/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
111023 18:58:29 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
111023 18:58:29 [Warning] Can't create test file /home/dargaud/.local/share/akonadi/db_data/penguin.lower-test
111023 18:58:29 [Note] Plugin 'FEDERATED' is disabled.
/usr/sbin/mysqld: Can't find file: './mysql/plugin.frm' (errno: 13)
111023 18:58:29 [ERROR] Can't open the mysql.plugin table. Please run mysql_upgrade to create it.
111023 18:58:29  InnoDB: Initializing buffer pool, size = 8.0M
111023 18:58:29  InnoDB: Completed initialization of buffer pool
111023 18:58:29  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'.
InnoDB: Cannot continue operation.
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x4168d4]
1: akonadiserver() [0x416c6c]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x36420) [0x7f3c1fb5a420]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35) [0x7f3c1fb5a3a5]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x17b) [0x7f3c1fb5db0b]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x11b) [0x7f3c2182843b]
6: akonadiserver() [0x4182e2]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xaf) [0x7f3c218b61ff]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x112943) [0x7f3c218be943]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x39) [0x7f3c218c77c9]
10: akonadiserver() [0x4124e6]
11: akonadiserver() [0x49a9d3]
12: akonadiserver() [0x418762]
13: akonadiserver() [0x419f2c]
14: akonadiserver() [0x41b567]
15: akonadiserver() [0x411ae2]
16: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f3c1fb4530d]
17: akonadiserver() [0x412371]
]
" 


Test 18:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 19:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```
Hint: if you google "Akonadi server process not registered at D-Bus", there's nothing helpful.

---

### Post by MWt on 2011-12-07
I've been fighting a very similar problem on 10.04LTS for several days (before that Kontact/Kmail made no problems since the 10.04 install in Apr 2010).

The kernel and its AppArmor module turned out to be the source of problems. I don't know the kernel version in 11.10, but in case it helps, here are the details. File content of '/home/mw/.local/share/akonadi/akonadiserver.error' was:
```
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld" 
arguments: ("--defaults-file=/home/mw/.local/share/akonadi//mysql.conf", "--datadir=/home/mw/.local/share/akonadi/db_data/", "--socket=/home/mw/.local/share/akonadi/db_misc/mysql.socket") 
stdout: "" 
stderr: "Could not open required defaults file: /home/mw/.local/share/akonadi//mysql.conf
Fatal error in defaults handling. Program aborted
111205 10:39:18 [Warning] Can't create test file /home/mw/.local/share/akonadi/db_data/wfitj135e.lower-test
111205 10:39:18 [Warning] Can't create test file /home/mw/.local/share/akonadi/db_data/wfitj135e.lower-test
111205 10:39:18 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!
111205 10:39:18 [ERROR] Aborting
111205 10:39:18 [Note] /usr/sbin/mysqld: Shutdown complete
```

After (unsuccessfully) trying all "akonadictl start/stop/restart" hints from many posts, [http://userbase.kde.org/Akonadi_4.4/Troubleshooting#Apparmor]("http://userbase.kde.org/Akonadi_4.4/Troubleshooting#Apparmor") reminded me of the fact, that I had installed 2.6.38-12 kernel from official updates repository several days earlier. So next I tried booting with the older kernel, from 2.6.32 series, and all problems disappeared! (Strange thing is that I don't remember the problems with akonadi happening just after this kernel upgrade - maybe it was something like 1-2 later, but I'm not sure at this point)

---

