---
title: "Kubuntu Startup Error"
date: 2009-02-28
forum: General Help
---

### Post by kevin11951 on 2009-02-28
```
Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration.
The following drivers are installed: QMYSQL3, QMYSQL.
Make sure the required driver is installed.

File content of '/root/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL

[QMYSQL]
Name=akonadi
User=
Password=
Options="UNIX_SOCKET=/root/.local/share/akonadi/db_misc/mysql.socket"
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
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.0.67-0ubuntu6 for debian-linux-gnu on i486 ((Ubuntu))


Test 4:  SUCCESS
--------

No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup into '/root/.local/share/akonadi/db_data/mysql.err'.

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
# log queries slower than n seconds, log file name relative to datadir
log_slow_queries=mysql.slow
long_query_time=1
# log queries not using indices, debug only, disable for production use
log_queries_not_using_indexes=1
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
Details: The MySQL server configuration was found at <a href='/root/.local/share/akonadi/mysql.conf'>/root/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/root/.local/share/akonadi/mysql.conf':
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
# log queries slower than n seconds, log file name relative to datadir
log_slow_queries=mysql.slow
long_query_time=1
# log queries not using indices, debug only, disable for production use
log_queries_not_using_indexes=1
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



Test 8:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi Control: stopped
Akonadi Server: stopped


Test 9:  ERROR
--------

Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 10:  ERROR
--------

Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 11:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 12:  ERROR
--------

No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to.

Directory listing of '/usr/share/akonadi/agents':
distlistresource.desktop
icalresource.desktop
imaplibresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
mailthreaderagent.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
distlistresource.desktop
icalresource.desktop
imaplibresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
mailthreaderagent.desktop
nepomukcontactfeeder.desktop
nepomukemailfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
strigifeeder.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share'

Test 13:  ERROR
--------

Current Akonadi server error log found.
Details: The Akonadi server did report error during startup into <a href='/root/.local/share/akonadi/akonadiserver.error'>/root/.local/share/akonadi/akonadiserver.error</a>.

File content of '/root/.local/share/akonadi/akonadiserver.error':
"[
0: akonadiserver(_Z10kBacktracev+0x35) [0x8052095]
1: akonadiserver [0x8052586]
2: [0xb80c7400]
3: [0xb80c7430]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x50) [0xb78ba8a0]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb78bc268]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x95) [0xb7c1c795]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8053284]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x9e) [0xb7ca9fbe]
9: /usr/lib/libQtCore.so.4 [0xb7cb6f8e]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0xb7cb7288]
11: /usr/lib/libakonadiprivate.so.1(_ZN6QDebugD1Ev+0x4f) [0xb7fc1f1f]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x1a8e) [0xb7fc94ce]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x72) [0xb7fcb232]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x56) [0xb7fcc336]
15: akonadiserver(main+0x398) [0x804d088]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb78a5685]
17: akonadiserver [0x804cc21]
]
" 


Test 14:  ERROR
--------

Previous Akonadi server error log found.
Details: The Akonadi server did report error during its previous startup into <a href='/root/.local/share/akonadi/akonadiserver.error.old'>/root/.local/share/akonadi/akonadiserver.error.old</a>.

File content of '/root/.local/share/akonadi/akonadiserver.error.old':
"[
0: akonadiserver(_Z10kBacktracev+0x35) [0x8052095]
1: akonadiserver [0x8052586]
2: [0xb804e400]
3: [0xb804e430]
4: /lib/tls/i686/cmov/libc.so.6(gsignal+0x50) [0xb78418a0]
5: /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7843268]
6: /usr/lib/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x95) [0xb7ba3795]
7: akonadiserver(_ZN15FileDebugStream9writeDataEPKcx+0xc4) [0x8053284]
8: /usr/lib/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0x9e) [0xb7c30fbe]
9: /usr/lib/libQtCore.so.4 [0xb7c3df8e]
10: /usr/lib/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x68) [0xb7c3e288]
11: /usr/lib/libakonadiprivate.so.1(_ZN6QDebugD1Ev+0x4f) [0xb7f48f1f]
12: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer20startDatabaseProcessEv+0x1a8e) [0xb7f504ce]
13: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServerC1EP7QObject+0x72) [0xb7f52232]
14: /usr/lib/libakonadiprivate.so.1(_ZN7Akonadi13AkonadiServer8instanceEv+0x56) [0xb7f53336]
15: akonadiserver(main+0x398) [0x804d088]
16: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb782c685]
17: akonadiserver [0x804cc21]
]
" 


Test 15:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 16:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.


```

I get this error from akonadi in kde 4.2 every time i turn the computer on, or start a pim app (eg. kopete)

---

### Post by lyjg0228 on 2009-02-28
&#36187;&#20107;&#35299;&#26512;:&#35834;&#22495;&#27835;,&#33324;&#23612;,&#24067;&#8230;   [**bet365**](http://www.bct365.cn/)&#30424;&#21475;&#20998;&#26512;:&#26757;&#36203;&#20262;,&#8230;    &#26364;&#32852;&#38431;&#39318;&#25112;&#36133;&#21271;&#65292;&#24343;&#26684;&#26862;&#8230;    &#21338;&#24425;&#20844;&#21496;&#24050;&#30447;&#19978;CBA &#24196;&#23478;&#8230;    nab:&#22799;&#27931;&#29305;&#40077;&#21187;&#29483; @ &#21326;&#30427;&#8230;    bet365&#19982;[**888&#30495;&#20154;**](http://www.bct365.cn/)&#26368;&#36817;&#36180;&#29575;&#8230;   [**bet365**](http://www.bct365.cn/)&#21672;&#35810;&#65306;&#32599;&#32435;&#23572;&#22810;&#21152;&#8230;    &#36187;&#20107;&#35299;&#26512;:&#20999;&#23572;&#35199;,&#22467;&#24343;&#39039;&#8230;    &#36180;&#29575;&#25512;&#20171;:&#38463;&#20185;&#22900;,&#38886;&#26681;,&#28909;&#8230;    &#30424;&#21475;&#20998;&#26512;:&#24067;&#40065;&#22622;&#23572;,&#25176;&#23572;&#8230;      &#12288;&#12288;bet365&#36275;&#29699;&#21160;&#24577; 888&#30495;&#20154;  &#31185;&#27604;&#30127;&#29378;&#39129;&#20998;&#38750;&#31109;&#24072;&#25152;&#24895;&#8230;   [**bet365**](http://www.bct365.cn/)&#65306;&#24067;&#21147;&#33324;&#27969;&#28010;VS&#26032;&#8230;    Bet365&#65306;&#29233;&#21326;&#39039;VS&#21033;&#29289;&#28006;&#8230;    Bet365&#65306;&#38463;&#22763;&#19996;&#32500;&#25289;VS&#21776;&#8230;   [**888&#30495;&#20154;**](http://www.bct365.cn/)&#65306;&#24067;&#21147;&#33324;&#27969;&#28010;VS&#26032;&#8230;    888&#30495;&#20154;&#65306;&#29233;&#21326;&#39039;VS&#21033;&#29289;&#28006;&#8230;    888&#30495;&#20154;&#65306;&#25343;&#27874;&#37324;VS&#31062;&#20113;&#36798;&#8230;    &#35874;&#20122;&#40857;&#21457;&#26126;&#21449;&#33136;&#32908;&#38647;&#20154;&#35789;&#8230;    &#21346;&#35199;&#22885;&#25351;&#23450;&#25308;&#20161;&#20013;&#21355;&#25509;&#29677;&#8230;    &#22836;&#21495;&#23556;&#25163;&#36973;&#22823;&#40132;6000&#19975;&#25253;&#8230;

---

### Post by sonicb00m on 2009-02-28
Same here, still trying to fix it.

Also, I cannot seem to get any visual app to ask for adminstration mode. Package manager and setting samba permissions in dolphin doesn't work.

GTK theming is also broken :(

Fresh install as well!

---

### Post by sonicb00m on 2009-03-01
Seems to be because of an encrypted home folder.

---

### Post by kevin11951 on 2009-03-02
I semi figured it out, if i use the root account to login, then it made the error, if i used my normal user account, it would work, no error.  could it have something to do with belonging to a certain group?

---

### Post by wayward4now on 2009-07-13
Did you ever get dbus resolved?? I just upgraded to jaunty and I'm seeing the very same problem. I held back upgrading long enough to hopefully miss out on all of the broken package funs, but it looks like I got bit after all! <grins> Ric

---

### Post by Justin Trouble on 2009-08-04
Check the owner and group permissions of /home/username/.local/share/akonadi

Mine was owned by root. I renamed the directory and the problem was resolved. After a restart the (recreated) akonadi directory was owned by me.

A couple of other directories in share/ were also owned by root, so I just renamed the share directory. Not sure if there are any implications, but I have the old directory there as a backup.

---

### Post by Freezewarp on 2009-12-31
For anyone else who has this problem or something similar, running AppArmor may prove problematic. I thought that this was a problem to me long before I installed AppArmor, but I'm not sure. Either running "/etc/init.d/apparmor stop" or seeing the instructions at [http://userbase.kde.org/Akonadi#Apparmor](http://userbase.kde.org/Akonadi#Apparmor) may help. Just a thought, as this helped me just now.

---

