---
title: "akonadi fail: &quot;process not registered at D-Bus&quot;"
date: 2016-02-04
forum: Desktop Environments
---

### Post by flips2 on 2016-02-04
Hi, half-arsed amateur Kubuntu 15.10 user here.

For a while now I haven't been able to use akonadi, which sucks, because I used to use it a lot.

When I attempt to start the server through the configuration GUI I get the error below. 

I tried commenting (and uncommenting) "sql_mode=strict_trans_tables" in mysql.conf, as described here [https://www.kubuntuforums.net/showthread.php?46905-SOLV-Akonadi-control-process-not-registered-at-D-Bus-Upgrade-Kde-4-3-5-to-4-4](https://www.kubuntuforums.net/showthread.php?46905-SOLV-Akonadi-control-process-not-registered-at-D-Bus-Upgrade-Kde-4-3-5-to-4-4)

But no joy. 

Any suggestions appreciated.

```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/flips/.config/akonadi/akonadiserverrc':
[Debug]
Tracer=null

[%General]
Driver=QMYSQL

[QMYSQL]
Host=
Name=akonadi
Options="UNIX_SOCKET=/tmp/akonadi-flips.RH7YMN/mysql.socket"
Password=
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true
User=

[QPSQL]
Host=
Name=akonadi
Password=
Port=5432
StartServer=true
User=

[SQLITE]
Name=akonadi


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
Details: MySQL server found: /usr/sbin/mysqld  Ver 5.6.28-0ubuntu0.15.10.1 for debian-linux-gnu on x86_64 ((Ubuntu))


Test 5:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file '<a href="/home/flips/.local/share/akonadi/db_data/mysql.err">/home/flips/.local/share/akonadi/db_data/mysql.err</a>' contains errors.

File content of '/home/flips/.local/share/akonadi/db_data/mysql.err':
2016-02-05 00:20:13 16173 [Note] Plugin 'FEDERATED' is disabled.
2016-02-05 00:20:13 7f2b7b7b0740 InnoDB: Warning: Using innodb_additional_mem_pool_size is DEPRECATED. This option may be removed in future releases, together with the option innodb_use_sys_malloc and with the InnoDB's internal memory allocator.
2016-02-05 00:20:13 16173 [Note] InnoDB: Using atomics to ref count buffer pool pages
2016-02-05 00:20:13 16173 [Note] InnoDB: The InnoDB memory heap is disabled
2016-02-05 00:20:13 16173 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
2016-02-05 00:20:13 16173 [Note] InnoDB: Memory barrier is not used
2016-02-05 00:20:13 16173 [Note] InnoDB: Compressed tables use zlib 1.2.8
2016-02-05 00:20:13 16173 [Note] InnoDB: Using Linux native AIO
2016-02-05 00:20:13 16173 [Note] InnoDB: Using CPU crc32 instructions
2016-02-05 00:20:13 16173 [Note] InnoDB: Initializing buffer pool, size = 80.0M
2016-02-05 00:20:13 16173 [Note] InnoDB: Completed initialization of buffer pool
2016-02-05 00:20:13 16173 [Note] InnoDB: Highest supported file format is Barracuda.
2016-02-05 00:20:13 16173 [Note] InnoDB: The log sequence numbers 4700234896 and 4700234896 in ibdata files do not match the log sequence number 4700438674 in the ib_logfiles!
2016-02-05 00:20:13 16173 [Note] InnoDB: Database was not shutdown normally!
2016-02-05 00:20:13 16173 [Note] InnoDB: Starting crash recovery.
2016-02-05 00:20:13 16173 [Note] InnoDB: Reading tablespace information from the .ibd files...
2016-02-05 00:20:13 16173 [ERROR] InnoDB: Attempted to open a previously opened tablespace. Previous tablespace mysql/innodb_table_stats uses space ID: 1 at filepath: ./mysql/innodb_table_stats.ibd. Cannot open tablespace akonadi/schemaversiontable which uses space ID: 1 at filepath: ./akonadi/schemaversiontable.ibd
2016-02-05 00:20:13 7f2b7b7b0740  InnoDB: Operating system error number 2 in a file operation.
InnoDB: The error means the system cannot find the path specified.
InnoDB: If you are installing InnoDB, remember that you must create
InnoDB: directories yourself, InnoDB does not create them.
InnoDB: Error: could not open single-table tablespace file ./akonadi/schemaversiontable.ibd
InnoDB: We do not continue the crash recovery, because the table may become
InnoDB: corrupt if we cannot apply the log records in the InnoDB log to it.
InnoDB: To fix the problem and start mysqld:
InnoDB: 1) If there is a permission problem in the file and mysqld cannot
InnoDB: open the file, you should modify the permissions.
InnoDB: 2) If the table is not needed, or you can restore it from a backup,
InnoDB: then you can remove the .ibd file, and InnoDB will do a normal
InnoDB: crash recovery and ignore that table.
InnoDB: 3) If the file system or the disk is broken, and you cannot remove
InnoDB: the .ibd file, you can set innodb_force_recovery > 0 in my.cnf
InnoDB: and force InnoDB to continue crash recovery here.


Test 6:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href="/etc/xdg/akonadi/mysql-global.conf">/etc/xdg/akonadi/mysql-global.conf</a>.

File content of '/etc/xdg/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris Köhntopp <kris@mysql.com>
#
[mysqld]

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables

# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");

# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)

#expire_logs_days=3

#sync_bin_log=0

# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb

# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:1M)
# Deprecated in MySQL >= 5.6.3
innodb_additional_mem_pool_size=1M

# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M

# Create a .ibd file for each table (default:0)
innodb_file_per_table=1

# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2

# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M

# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M

# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err

# print warnings and connection errors (default:1)
log_warnings=2

# Convert table named to lowercase
lower_case_table_names=1

# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M

# Maximum simultaneous connections allowed (default:100)
max_connections=256

# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)

# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0

# Do not cache results (default:1)
query_cache_type=0

# Do not use the privileges mechanisms
skip_grant_tables

# Do not listen for TCP/IP connections at all
skip_networking

# The number of open tables for all threads. (default:64)
table_open_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href="/home/flips/.local/share/akonadi/mysql.conf">/home/flips/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/flips/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris Köhntopp <kris@mysql.com>
#
[mysqld]

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables

# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");

# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)

#expire_logs_days=3

#sync_bin_log=0

# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb

# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:1M)
# Deprecated in MySQL >= 5.6.3
innodb_additional_mem_pool_size=1M

# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M

# Create a .ibd file for each table (default:0)
innodb_file_per_table=1

# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2

# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M

# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M

# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err

# print warnings and connection errors (default:1)
log_warnings=2

# Convert table named to lowercase
lower_case_table_names=1

# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M

# Maximum simultaneous connections allowed (default:100)
max_connections=256

# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)

# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0

# Do not cache results (default:1)
query_cache_type=0

# Do not use the privileges mechanisms
skip_grant_tables

# Do not listen for TCP/IP connections at all
skip_networking

# The number of open tables for all threads. (default:64)
table_open_cache=200

# How many threads the server should cache for reuse (default:0)
thread_cache_size=3

# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000

# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 5.0.51


Test 10:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 12:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 13:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share/plasma:/usr/local/share/:/usr/share/'; make sure this includes all paths where Akonadi agents are installed.

Directory listing of '/usr/share/akonadi/agents':
akonadibalooindexingagent.desktop
akonotesresource.desktop
archivemailagent.desktop
birthdaysresource.desktop
contactsresource.desktop
davgroupwareresource.desktop
followupreminder.desktop
googlecalendarresource.desktop
googlecontactsresource.desktop
icaldirresource.desktop
icalresource.desktop
imapresource.desktop
invitationsagent.desktop
kalarmdirresource.desktop
kalarmresource.desktop
kolabresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mailfilteragent.desktop
mboxresource.desktop
migrationagent.desktop
mixedmaildirresource.desktop
newmailnotifieragent.desktop
notesagent.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
sendlateragent.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share/plasma:/usr/local/share/:/usr/share/'

Test 14:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href="/home/flips/.local/share/akonadi/akonadiserver.error">/home/flips/.local/share/akonadi/akonadiserver.error</a>.

File content of '/home/flips/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/flips/.local/share/akonadi/mysql.conf", "--datadir=/home/flips/.local/share/akonadi/db_data/", "--socket=/tmp/akonadi-flips.RH7YMN/mysql.socket") 
stdout: "" 
stderr: "2016-02-05 00:20:13 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2016-02-05 00:20:13 0 [Note] /usr/sbin/mysqld (mysqld 5.6.28-0ubuntu0.15.10.1) starting as process 16173 ...
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x57e396]
1: akonadiserver() [0x57e6be]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x352f0) [0x7fbc666d82f0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x37) [0x7fbc666d8267]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x16a) [0x7fbc666d9eca]
5: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_Z17qt_message_output9QtMsgTypeRK18QMessageLogContextRK7QString+0x185) [0x7fbc670963d5]
6: akonadiserver() [0x580cbc]
7: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN9QIODevice5writeEPKcx+0x10b) [0x7fbc671b149b]
8: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(+0x1bca26) [0x7fbc671c2a26]
9: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN11QTextStreamD2Ev+0x11b) [0x7fbc671c2c6b]
10: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN6QDebugD1Ev+0x3f) [0x7fbc67193bdf]
11: akonadiserver() [0x4974ea]
12: akonadiserver() [0x420b09]
13: akonadiserver() [0x422177]
14: akonadiserver() [0x503329]
15: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN7QObject5eventEP6QEvent+0xf1) [0x7fbc672b9651]
16: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0xbc) [0x7fbc67287efc]
17: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x2c7) [0x7fbc6728a057]
18: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(+0x2d8e73) [0x7fbc672dee73]
19: /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x2a7) [0x7fbc650fbff7]
20: /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4a250) [0x7fbc650fc250]
21: /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c) [0x7fbc650fc2fc]
22: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN20QEventDispatcherGlib13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x5f) [0x7fbc672df27f]
23: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0x10a) [0x7fbc6728575a]
24: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN16QCoreApplication4execEv+0x9c) [0x7fbc6728d2cc]
25: akonadiserver() [0x41fa79]
26: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7fbc666c3a40]
27: akonadiserver(_start+0x29) [0x4204e9]
]
" 


Test 15:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href="/home/flips/.local/share/akonadi/akonadiserver.error.old">/home/flips/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/home/flips/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/flips/.local/share/akonadi/mysql.conf", "--datadir=/home/flips/.local/share/akonadi/db_data/", "--socket=/tmp/akonadi-flips.RH7YMN/mysql.socket") 
stdout: "" 
stderr: "2016-02-05 00:20:08 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2016-02-05 00:20:08 0 [Note] /usr/sbin/mysqld (mysqld 5.6.28-0ubuntu0.15.10.1) starting as process 16159 ...
" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x57e396]
1: akonadiserver() [0x57e6be]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x352f0) [0x7f9b5282c2f0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x37) [0x7f9b5282c267]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x16a) [0x7f9b5282deca]
5: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_Z17qt_message_output9QtMsgTypeRK18QMessageLogContextRK7QString+0x185) [0x7f9b531ea3d5]
6: akonadiserver() [0x580cbc]
7: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN9QIODevice5writeEPKcx+0x10b) [0x7f9b5330549b]
8: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(+0x1bca26) [0x7f9b53316a26]
9: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN11QTextStreamD2Ev+0x11b) [0x7f9b53316c6b]
10: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN6QDebugD1Ev+0x3f) [0x7f9b532e7bdf]
11: akonadiserver() [0x4974ea]
12: akonadiserver() [0x420b09]
13: akonadiserver() [0x422177]
14: akonadiserver() [0x503329]
15: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN7QObject5eventEP6QEvent+0xf1) [0x7f9b5340d651]
16: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0xbc) [0x7f9b533dbefc]
17: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x2c7) [0x7f9b533de057]
18: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(+0x2d8e73) [0x7f9b53432e73]
19: /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_dispatch+0x2a7) [0x7f9b5124fff7]
20: /lib/x86_64-linux-gnu/libglib-2.0.so.0(+0x4a250) [0x7f9b51250250]
21: /lib/x86_64-linux-gnu/libglib-2.0.so.0(g_main_context_iteration+0x2c) [0x7f9b512502fc]
22: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN20QEventDispatcherGlib13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x5f) [0x7f9b5343327f]
23: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0x10a) [0x7f9b533d975a]
24: /usr/lib/x86_64-linux-gnu/libQt5Core.so.5(_ZN16QCoreApplication4execEv+0x9c) [0x7f9b533e12cc]
25: akonadiserver() [0x41fa79]
26: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0) [0x7f9b52817a40]
27: akonadiserver(_start+0x29) [0x4204e9]
]
" 


Test 16:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 17:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```

---

