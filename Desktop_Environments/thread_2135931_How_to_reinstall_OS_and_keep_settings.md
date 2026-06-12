---
title: "How to reinstall OS and keep settings?"
date: 2013-04-15
forum: Desktop Environments
---

### Post by TheChristianHippie on 2013-04-15
Ok, I posted earlier about Akonadi problems ([http://ubuntuforums.org/showthread.php?t=2131813&p=12585887#post12585887](http://ubuntuforums.org/showthread.php?t=2131813&p=12585887#post12585887)) and apparently it's such a new program NO ONE knows how to troubleshoot or fix it so I guess I have no choice but a fresh install to restore it. The trouble is I don't want to lose all my settings and installed themes, icons, styles etc. let alone my files in /home......

Is there a way to do a fresh install/reinstall and KEEP all my settings? This is a kubuntu desktop environment over ubuntu-remix on a 64bit win8 OES machine. I have a separate /home partition. Thanks all! :KS

---

### Post by oldfred on 2013-04-16
If you have a separate /home, you can use manual install, choose existing / (root) partition for new root, choose format - ext4. Also choose the existing /home but DO NOT FORMAT it, just choose it. It should automatically find swap and choose to reinstall grub to MBR of same drive.

IF you have installed a lot of apps you can export a list to make it easy to reinstall.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But it is always best to have good backups and perhaps a few more things to include.
      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

 Some files to exclude from /home backup:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by oldos2er on 2013-04-16
A better place to look for help with Akonadi is here: [http://forum.kde.org/search.php](http://forum.kde.org/search.php)

Have you tried disabling it?

---

### Post by hainen on 2013-04-16
If I remeber correct, when I had problem with Akonadi it was a becaouse old incorrect akonadi agent configurations. You has the configuration interface in the akonadi console or in the akonadi configuration application

---

### Post by TheChristianHippie on 2013-04-18
Thank you OldFred :) I have been attempting to follow your directions and the directions in the links provided, but in my attempts to backup /home and /etc I cannot get ALL files to copy over. I have been attempting to copy/paste the folders over to an external hard drive, but I keep getting error messages, "could not read" or "could not enter" for certain files, like the "lost + found" file and various files in /etc. How do I get these folders to copy over COMPLETELY? Is there a better method to backup these files on my external HD? I haven't gone much further in the process since I'm kind of stuck here.

Oldos2er: Thank you for your suggestion, but I couldn't find anything on that forumn that could help. I tried, uninstalling re-installing akonadi as well as recreating it, deleting it and restarting it etc... no dice :(

Hainen: Thank you for your advice.... I don't understand though? > [COLOR=#000000]You has the configuration interface in the akonadi console or in the akonadi configuration application [/COLOR]I installed the console for akonadi, but it failed to start: "Failed to connect to database: Can't connect to local MySQL server through socket '/home/rachel/.local/share/akonadi/socket-Artax3ubuntu/mysql.socket' (2) QMYSQL: Unable to connect" and here's error report: 

```
Akonadi Server Self-Test Report
===============================


Test 1:  SUCCESS
--------


Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.


File content of '/home/rachel/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL


[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/home/rachel/.local/share/akonadi/socket-Artax3ubuntu/mysql.socket"
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
Details: MySQL server found: /usr/sbin/mysqld  Ver 5.5.29-0ubuntu0.12.10.1 for debian-linux-gnu on x86_64 ((Ubuntu))




Test 5:  SUCCESS
--------


No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup. The log can be found in '/home/rachel/.local/share/akonadi/db_data/mysql.err'.


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
table_cache=200


# How many threads the server should cache for reuse (default:0)
thread_cache_size=3


# wait 365d before dropping the DB connection (default:8h)
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
Details: The MySQL server configuration was found at <a href='/home/rachel/.local/share/akonadi/mysql.conf'>/home/rachel/.local/share/akonadi/mysql.conf</a> and is readable.


File content of '/home/rachel/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
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
table_cache=200


# How many threads the server should cache for reuse (default:0)
thread_cache_size=3


# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000


[client]
default-character-set=utf8




Test 9:  SUCCESS
--------


akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.8.1




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
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share/kde-plasma:/usr/local/share/:/usr/share/'; make sure this includes all paths where Akonadi agents are installed.


Directory listing of '/usr/share/akonadi/agents':
akonadinepomukfeederagent.desktop
akonotesresource.desktop
archivemailagent.desktop
birthdaysresource.desktop
contactsresource.desktop
davgroupwareresource.desktop
facebookresource.desktop
googlecalendarresource.desktop
googlecontactsresource.desktop
icalresource.desktop
imapresource.desktop
invitationsagent.desktop
kabcresource.desktop
kalarmdirresource.desktop
kalarmresource.desktop
kcalresource.desktop
kdeaccountsresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mailfilteragent.desktop
mboxresource.desktop
microblog.desktop
mixedmaildirresource.desktop
mtdummyresource.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop


Environment variable XDG_DATA_DIRS is set to '/usr/share/kde-plasma:/usr/local/share/:/usr/share/'


Test 15:  ERROR
--------


Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href='/home/rachel/.local/share/akonadi/akonadiserver.error'>/home/rachel/.local/share/akonadi/akonadiserver.error</a>.


File content of '/home/rachel/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/rachel/.local/share/akonadi/mysql.conf", "--datadir=/home/rachel/.local/share/akonadi/db_data/", "--socket=/home/rachel/.local/share/akonadi/socket-Artax3ubuntu/mysql.socket") 
stdout: "" 
stderr: "130327  1:19:37 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130327  1:19:37 [ERROR] Aborting


130327  1:19:37 [Note] /usr/sbin/mysqld: Shutdown complete


" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x4188c4]
1: akonadiserver() [0x418c01]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7f2e972e54a0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35) [0x7f2e972e5425]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x17b) [0x7f2e972e8b8b]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x122) [0x7f2e98d984c2]
6: akonadiserver() [0x41aafb]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xb4) [0x7f2e98e327c4]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x11645f) [0x7f2e98e3d45f]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3b) [0x7f2e98e45a5b]
10: akonadiserver() [0x48c7aa]
11: akonadiserver() [0x41b857]
12: akonadiserver() [0x41c7d5]
13: akonadiserver() [0x41ddf7]
14: akonadiserver() [0x411ce3]
15: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7f2e972d076d]
16: akonadiserver() [0x412641]
]
" 




Test 16:  ERROR
--------


Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href='/home/rachel/.local/share/akonadi/akonadiserver.error.old'>/home/rachel/.local/share/akonadi/akonadiserver.error.old</a>.


File content of '/home/rachel/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/rachel/.local/share/akonadi/mysql.conf", "--datadir=/home/rachel/.local/share/akonadi/db_data/", "--socket=/home/rachel/.local/share/akonadi/socket-Artax3ubuntu/mysql.socket") 
stdout: "" 
stderr: "130327  1:19:37 [ERROR] Fatal error: Please read "Security" section of the manual to find out how to run mysqld as root!


130327  1:19:37 [ERROR] Aborting


130327  1:19:37 [Note] /usr/sbin/mysqld: Shutdown complete


" 
exit code: 1 
process error: "Unknown error" 
"[
0: akonadiserver() [0x4188c4]
1: akonadiserver() [0x418c01]
2: /lib/x86_64-linux-gnu/libc.so.6(+0x364a0) [0x7fcc9ad7f4a0]
3: /lib/x86_64-linux-gnu/libc.so.6(gsignal+0x35) [0x7fcc9ad7f425]
4: /lib/x86_64-linux-gnu/libc.so.6(abort+0x17b) [0x7fcc9ad82b8b]
5: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_Z17qt_message_output9QtMsgTypePKc+0x122) [0x7fcc9c8324c2]
6: akonadiserver() [0x41aafb]
7: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN9QIODevice5writeEPKcx+0xb4) [0x7fcc9c8cc7c4]
8: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(+0x11645f) [0x7fcc9c8d745f]
9: /usr/lib/x86_64-linux-gnu/libQtCore.so.4(_ZN11QTextStreamD1Ev+0x3b) [0x7fcc9c8dfa5b]
10: akonadiserver() [0x48c7aa]
11: akonadiserver() [0x41b857]
12: akonadiserver() [0x41c7d5]
13: akonadiserver() [0x41ddf7]
14: akonadiserver() [0x411ce3]
15: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fcc9ad6a76d]
16: akonadiserver() [0x412641]
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

The configuration tools also fail to start, same errors. Nothing akonadi related works.

---

### Post by oldfred on 2013-04-18
For backup I use rsync with sudo. But some folders you really do not need like lost & found. When you create a new file system it will create a new lost & found. And there are a couple of lock files in /home that as long as you are logged in will not let you copy them. But again they only exist when you are using system.

---

### Post by TheChristianHippie on 2013-04-18
Are they (the files in the lost&found folder, and the ones in /etc that won't transfer) necessary to keep my settings? If not, could I just ignore them? They will be installed with the new install right? Is there a chance that if I restore my settings with the backed up files I may just transfer over my current akonadi problem to the new installation? > [COLOR=#000000]And there are a couple of lock files in /home that as long as you are logged in will not let you copy them. But again they only exist when you are using system.[/COLOR] So I don't really need them to preserve my settings in a new install?

---

### Post by oldfred on 2013-04-18
Most are files & folders that you need & should copy. If not using command line be sure to include all the hidden files & folders. Data can be copied to NTFS, but any system files will lose ownership & permissions and may cause issues. Best to use Linux formatted partition.

---

### Post by TheChristianHippie on 2013-04-19
Ok. I have partitioned an ext4 partition onto my external hard drive. If I use the konsole terminal to copy over the files for backup, will they all copy over? How would I do that exactly? Thanks for your patient help :)

---

### Post by TheChristianHippie on 2013-04-19
Hit another road block. Could not write to my new linux partition on my EHDD. Found this link: [http://ubuntuforums.org/showthread.php?t=1334840](http://ubuntuforums.org/showthread.php?t=1334840)
But commands aren't working. Here's how things have gone so far:

```
rachel@Artax3ubuntu:~$ sudo fdisk -l
[sudo] password for rachel: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xeffa0c70


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x551b0dcf


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   481216511   240608224+   7  HPFS/NTFS/exFAT
/dev/sdb2       481216512   586072063    52427776   83  Linux
rachel@Artax3ubuntu:~$ sudo chown -R $USER:$USER </dev/sdb2>
bash: syntax error near unexpected token `newline'
rachel@Artax3ubuntu:~$ sudo chown -R $USER:$USER </dev/sdb2>
bash: syntax error near unexpected token `newline'
rachel@Artax3ubuntu:~$ sudo chmod -R 777 </dev/sdb2>
bash: syntax error near unexpected token `newline'
rachel@Artax3ubuntu:~$

```

What does "syntax error near unexpected token `newline'" mean? Does it mean I typed something in wrong? How can I get write permissions to my new partition? Also there is a "lost&found" folder in it! Where'd that come from?

Found out the difference between "mount point" and "partition" labels.... I think. Still no success:

```
 rachel@Artax3ubuntu:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda9 on /home type ext4 (rw)
/dev/sda2 on /boot/efi type vfat (rw)
gvfsd-fuse on /run/user/rachel/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=rachel)
/dev/sdb1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb2 on /media/ubuntu backup pa type ext4 (rw,nosuid,nodev,uhelper=udisks)
rachel@Artax3ubuntu:~$ sudo chown -R $USER:$USER </media/ubuntu backup pa>
bash: syntax error near unexpected token `newline'
rachel@Artax3ubuntu:~$ sudo chmod -R +w </media/ubuntu backup pa>
bash: syntax error near unexpected token `newline'
rachel@Artax3ubuntu:~$ 
```

---

### Post by oldfred on 2013-04-19
You do not type the <> as I assume you saw an example that use that for you to add your device.

Actual example, but you have to change to your mount point and device.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

Lost and found is automatically created with a new Linux partition.

---

### Post by TheChristianHippie on 2013-04-20
Ok, I have like A MILLION QUESTIONS, sorry:

> [COLOR=#000000]#if not known to list partitions, change sda5 to your data partition or create multiples with different mount points[/COLOR]

What does ^ that mean? I think the two partitions on my EHDD are listed as:
Device Boot            Start            End           Blocks       Id    System/dev/sdb1                  63   481216511   240608224+       7     HPFS/NTFS/exFAT
/dev/sdb2       481216512   586072063      52427776      83     Linux



[FONT=Ubuntu Mono][COLOR=#000000]sdb1 is the original partition which I shrank to make room for the new linux partition sdb2. So if they are listed are they "known to list partitions"? I don't know if what I created was a "data partition" unless that means a partitioned created for data rather than an OS... then that's what sdb1 and sdb2 are..... I have no idea how to "create multiples with different mount points". I assume you mean multiple partitions? Don't they usually have their own mount point? You mean the "mount as" option in gparted? what would I mount it as? I think I can just change sda5 to sdb2.... right?[/COLOR][/FONT]

> [COLOR=#000000]chmod -R a+rwX,o-w /mnt/data[/COLOR]
[COLOR=#000000]# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.[/COLOR]

This is actually terrifying, what does recursion mean? What does "everything is changed" mean?? Won't it reformat something? How do I NOT run it on a system partition? Isn't everything I do on a computer on a system partition? unless "system partition" means partition with the OS on it? Then I think it's safe to run it on sdb2.... nothing but the lost&found folder on that right now....
 
> [COLOR=#000000]#All directories will be 775.[/COLOR]
[COLOR=#000000]#All files will be 664 except those that were set as executable to begin with.[/COLOR]
[COLOR=#000000]sudo chown $USER:$USER /mnt/data[/COLOR] 

I don't know what this^ means. Will that be AFTER I get the files moved over? Directories will be labelled 775* and files named 664*? Do directories = folders?

Thank you for your patience :)

I've done up to this command "[COLOR=#000000]chmod -R a+rwX,o-w /mnt/data[/COLOR]" I'll do the rest once I understand better what I am doing :)

---

### Post by oldfred on 2013-04-20
Recursion means it will also change sub-folders all the way down. Without -R it only changes the folder you run the command from or the folder you specify.
System partition is the operating system and even /home is part of operating system. But data partitions with Linux format need you to set mount, set ownership & set permissions to easily use. NTFS does not support Linux ownership and permissions, so you can only set one default as part of how you mount it.
Some users accidentally change to / (root) or even mis-type a command so system thinks you mean root and then you change all the system ownership and permissions. And not everything is just root and permissions vary. Almost impossible to fix, so a reinstall is then required. But if you just run on data partitions and folders (directories) you then give yourself ownership and permission to use the files & folders.

Lots of detail if interested:
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

I added an example of one of my data folders. I link it into /home so it looks like it is a folder in /home but it really is in my data partition. I added the permissions in Nautilus to show them.

---

### Post by TheChristianHippie on 2013-04-20
Another snag :( What happened? What now?

```
 rachel@Artax3ubuntu:~$ sudo mkdir /mnt/data
rachel@Artax3ubuntu:~$ sudo mount /dev/sdb2 /mnt/data
rachel@Artax3ubuntu:~$ chmod -R a+rwX,o-w /mnt/data
chmod: changing permissions of `/mnt/data': Operation not permitted
chmod: changing permissions of `/mnt/data/lost+found': Operation not permitted
chmod: cannot read directory `/mnt/data/lost+found': Permission denied
rachel@Artax3ubuntu:~$ 

```

---

### Post by oldfred on 2013-04-20
You need sudo to change ownership & permissions, looks like I left that out, sorry.
I find I still forget sudo many times, it gives me the rasberries and I add sudo.

But in our household sudo does not always work. Usually it is make it yourself.
 [http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by TheChristianHippie on 2013-04-21
> [COLOR=#000000]But in our household sudo does not always work. Usually it is make it yourself.[/COLOR]
[http://xkcd.com/149/](http://xkcd.com/149/)

Lol! :D I should try that here! 

"sudo" worked for this at least! :) I copy/pasted the "my packages" file over to the new linux partition! :D Now, how do I get the entirety of the /home and /etc folders to copy over?  I tried to start down your list here: [http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541) again, and /home still doesn't fully copy over. "failed to enter" error came up about the "lost&found" folder. Should I use command line? How do I do that? Do hidden files copy over automatically when I copy/paste /home from / (root)?

---

### Post by oldfred on 2013-04-21
Lost & found should not matter, and there are a couple of lock files only open when you are booted that do not matter. If running from a liveCD then you would not even have those files to copy. 

With Linux it depends on what command you used to copy. With cp command you have to use -a switch to include hidden files. I use rsync as part of my backup script and it also needs switches to include hidden files. If scripting the copy you can also exclude a lot of temporary files and caches that are not vital. See man cp or man rsync although the man rsync it intimidating as it has so many options. I just found a few threads and sites with examples of rsync and used a combination of them.

 Originally Posted by MountainX View Post #20 also other backup apps  - also has some info on rsync switches.
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)


 Some files to exclude from /home backup - post by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by TheChristianHippie on 2013-04-22
Ok, been studying these threads. They aren't very specific. There's alot of assumed knowledge, for which I as a clueless n00b, have no reference points. 

MountainX mentioned a pretty simple sounding backup program, "storebackup", but when I go to the page it doesn't really have a simple download situation. The download page is a list of links to files, and I have no idea how to install those files (the adventure in attempting installation of similar files, i.e. icons, is what left me in this predicament). I installed rsync, and hit "run" but nothing happened. I assume it must be a command line program? So I'm at MountianX's #20 post, and wondering what to do with this text file I created. How does rsync know where I want the backup created? How do I do a "dry run"? Post #16 seems to be a starting point. But how do I tell rsync WHERE to put the backup files? What is "cron" and what is a "cron job"?

---

### Post by oldfred on 2013-04-22
There is grsync which is a gui for rsync. I have not used it but it may be easier for a new user.
But in the script you have to have a place to copy to. I create a mount and just happen to call it backup. And then I mount that backup from my backup partition. Then I copy to my backup partition.

This is part of my script. I also have another file that is the excludes list as I do not want to copy a long list of misc stuff, caches, temp files etc. If you have created mount and mounted a partition you do not have to do that and can just run the one line that is rsync.

> # ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

rsync -aruvlP /mnt/data/Documents /mnt/backup
rsync -aruvlP /mnt/data/Projects /mnt/backup
rsync -aruvlP /mnt/data/Notebooks /mnt/backup
rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup

Cron is the scheduling tool. It runs in the background and will run a task on a predetermined schedule, daily, weekly etc.
       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

---

### Post by TheChristianHippie on 2013-04-23
Ok, I think I'm ready to run one of these scripts, but I have three to choose from:

your most recent:
```
[COLOR=#000000]*# ! not *[/COLOR]
[COLOR=#000000]*if [ ! -d /mnt/backup ]; then*[/COLOR]
[COLOR=#000000]*mkdir /mnt/backup*[/COLOR]
[COLOR=#000000]*fi*[/COLOR]

[COLOR=#000000]*mount -t ext3 /dev/sda2 /mnt/backup*[/COLOR]

[COLOR=#000000]*rsync -aruvlP /mnt/data/Documents /mnt/backup*[/COLOR]
[COLOR=#000000]*rsync -aruvlP /mnt/data/Projects /mnt/backup*[/COLOR]
[COLOR=#000000]*rsync -aruvlP /mnt/data/Notebooks /mnt/backup*[/COLOR]
[COLOR=#000000]*rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup*[/COLOR]
```

I assume where you put, "[COLOR=#000000]*/dev/sda2 /mnt/backup*[/COLOR]" I would put "[COLOR=#000000][FONT=Ubuntu Mono]/dev/sdb2 /mnt/data[/FONT][/COLOR]"? Would I put /mnt/data everywhere you put /mnt/backup since I don't really think my mount is named anything. Or is it "[COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa[/FONT][/COLOR]" since I labelled the partition "ubuntu backup pa"--rtition. (I didn't know the character limit). Your switch is "-aruvIP" while MountainX's is "-avvP" or "-avP". What's the difference? Do I not need to worry about the text file after all?

Here's Mountain X's:
```
[COLOR=#000000]rsync [options] /source /destination[/COLOR]

[COLOR=#000000]rsync -avP /home /media/backup[/COLOR]
[COLOR=#000000]rsync -avP /share /media/backup[/COLOR]
[COLOR=#000000]rsync -avP /media/floppy /media/backup[/COLOR]
[COLOR=#000000]rsync -avP /etc /media/backup[/COLOR]
```

or from the text file:


> 
[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]# [/COLOR][COLOR=#417394]backup[/COLOR][COLOR=#000000] script[/COLOR]
[COLOR=#000000]echo "starting..."[/COLOR]
[COLOR=#000000]rsync -avvP /home /media/backup[/COLOR]
[COLOR=#000000]rsync -avvP /share /media/backup[/COLOR]
[COLOR=#000000]rsync -avvP /media/floppy /media/backup[/COLOR]
[COLOR=#000000]rsync -avvP /etc /media/backup[/COLOR]
[COLOR=#000000]echo "done"[/COLOR]
[COLOR=#000000]exit 0[/COLOR]

For the first one, the /source and /destination parts? Do I put my "[COLOR=#000000][FONT=Ubuntu Mono]/dev/sdb2 /mnt/data[/FONT][/COLOR]" as the /destination? What do I put as /source? Why the difference between -avvP and -avP? Do I really need the /floppy backup? Where do I include these from your list? 

> [COLOR=#000000]
1. /home (Users' personal files and settings)[/COLOR]
[COLOR=#000000]2. /etc (System-wide configuration settings)[/COLOR]
[COLOR=#000000]3. /var/spool/cron/crontabs (Commands which run automatically)[/COLOR]
[COLOR=#000000]4. The script to generate the backup[/COLOR]
[COLOR=#000000]5. list of installed applications [/COLOR]

[COLOR=#000000]I include these also:[/COLOR]
[COLOR=#000000]cp /etc/apt/sources.list ~/sources.list.backup[/COLOR]
[COLOR=#000000]apt-key exportall > ~/repositories.key[/COLOR]
[COLOR=#000000]Various hardware listings/configurations[/COLOR]
[COLOR=#000000]dpkg --get-selections > ubuntu-files[/COLOR]
[COLOR=#000000]bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh[/COLOR]
[COLOR=#000000]lshw -html > ~/hardware_info.html[/COLOR]
[COLOR=#000000]udevadm info --export-db > file.txt[/COLOR]
[COLOR=#000000]dmidecode > bios.txt[/COLOR]


From what I understand, my code in terminal would look like this (questions and changes in BOLD): [COLOR=#000000]


rsync [options] /**???** [/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/dev/sdb2 "/mnt/data" or "[/FONT][/COLOR]****[COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa"[/FONT][/COLOR]**

[COLOR=#000000]rsync -av**(v?)**P /home [/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa[/FONT][/COLOR]**
[COLOR=#000000]rsync -[/COLOR][COLOR=#000000]av[/COLOR]**(v?)**[COLOR=#000000]P[/COLOR][COLOR=#000000] /share [/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa[/FONT][/COLOR]**
[COLOR=#000000]rsync -[/COLOR][COLOR=#000000]av[/COLOR]**(v?)**[COLOR=#000000]P[/COLOR][COLOR=#000000] /media/floppy [/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa[/FONT][/COLOR]**
[COLOR=#000000]rsync -[/COLOR][COLOR=#000000]av[/COLOR]**(v?)**[COLOR=#000000]P[/COLOR][COLOR=#000000] /etc [/COLOR][B][COLOR=#000000][FONT=Ubuntu Mono]/media/ubuntu backup pa

Or -[/FONT][/COLOR][COLOR=#000000]*aruvlP*[/COLOR][/B][COLOR=#000000][I]?
[/I][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Or would it be easier to use the grsync program? Attached are some screen caps of the different windows, which "switches" should I check? I'll have it from /home to media/ubuntu backup pa and then make /home into /etc. Do I really need /share or /media/floppy? Cause your list only says /home and /etc and then specific folders, lists, or files.... 

[/FONT][/COLOR]

---

### Post by oldfred on 2013-04-23
I just run those other commands to have up to date copies of my system configuration in /home as part of my backup. Then I know how system was configured in worst case that I have to do major recovery.

I have these in my script so I know what the settings are. Some may be overlaps?

# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

source is the first path and destination is second path separated by a space. You do have to have those as mount points.

You should not use spaces with Linux as it makes it difficult to use in commands. You then have to add quotes or "escape" the space character and it seems to vary how to do that. I just use under_score, CamelCase, or justonename.

Another update.
It really is best just to define a rsync command and run it in test mode on your system. Then once you actually get that to work copy it into a script. 
Many of my scripts are a copy of commands from history with lots of editing as the history has lots of mistakes.

---

### Post by TheChristianHippie on 2013-04-24
Ok! Used grsync to backup /home and /etc, though some akonadi files wouldn't copy (which is ok cause I don't want that broke junk) and 3-4 /etc files.... but it may be enough. I used all the code we had gone through to decipher which switches I wanted selected. I think I got it. Now started going down this list:
> [COLOR=#000000]cp /etc/apt/sources.list ~/sources.list.backup[/COLOR]
[COLOR=#000000]apt-key exportall > ~/repositories.key[/COLOR]
[COLOR=#000000]Various hardware listings/configurations[/COLOR]
[COLOR=#000000]dpkg --get-selections > ubuntu-files[/COLOR]
[COLOR=#000000]bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh[/COLOR]
[COLOR=#000000]lshw -html > ~/hardware_info.html[/COLOR]
[COLOR=#000000]udevadm info --export-db > file.txt[/COLOR]
[COLOR=#000000]dmidecode > bios.txt
[/COLOR]
Where is "[COLOR=#000000]cp /etc/apt/sources.list ~/sources.list.backup"? or are those commands for terminal?

Oh and a good question: My backing up my settings and such won't preserve the akonadi errors will it? Like when I "restore" or whatever my backups, they shouldn't break the akonadi reinstall will they? I'm not backing up my problem right? Also what about backing up google chrome? Bookmarks/settings? They didn't transfer from my previous computer to this one through my "profile" so is there another way to do it?[/COLOR]

---

### Post by oldfred on 2013-04-24
The commands you just posted were the ones I use to save some system settings into my /home or folders so when I run the rsync to backup /home it includes those. Those are bash commands as shown. With sudo you can run in the terminal.

If you backup all of /home including hidden files & folders and have not previously moved Firefox or Chromium profiles somewhere else they should be in your backup. You may have to turn show hidden files on to see them?

This was just for me as it is my file structure and bootinfoscipt is now version 61 and does not have the number in the command. I have updated mine, but you will not have those folders. And unless you have downloaded bootinfoscript you will not have it to run. 

All those commands are run from my bash file. When testing and running from command line they need sudo.

You have Documents but I added under Documents the rest of this:
[COLOR=#000000]bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh[/COLOR]

---

### Post by TheChristianHippie on 2013-04-27
Ok. I reinstalled my OS. Things did NOT go smoothly. I inserted the CD and chose "something else" and mounted my linux partitions the same as I had before, except not reformatting /home. It said install successful..... no boot. Just black screen. Repeated this process 3 times. same results. Then chose "repair install ubuntu remix" option. Same result. No boot, just black screen. Last time chose "erase ubuntu remix and reinstall" option. UBUNTU BOOTED! But ONLY ubuntu o.O
Now everytime I restart, ubuntu starts right up, NO GRUB menu to be seen. Where'd grub go? How do I get it back?

---

### Post by oldfred on 2013-04-27
If only one system found by grub2's os-prober, you do not get menu as it is not needed unless you have issues. You should be able to get to menu by holding shift key from BIOS until menu appears.

If you have other systems, try this, but it should have run as part of install. It also runs the os-prober.
sudo update-grub

If still issues post link to BootInfo report from Boot-Repair.

---

### Post by TheChristianHippie on 2013-04-27
Alright, got a grub menu by running boot-repair from inside Ubuntu. But no matter. WINDOWS IS GONE. Apparently this option:

> Erase Ubuntu-Secure-Remix 12.10 30nov2012 and reinstall
Warning** This will delete all your Ubuntu-Secure-Remix 12.10 30nov2012 programs,documents,photos,music, and any other files.

Actually means that NOT ONLY "Ubuntu-Secure-Remix 12.10 30nov2012 programs,documents,photos,music, and any other files" will be erased and reinstalled** BUT THE WHOLE HDD will be reformatted**, you will lose all your partitions and data, and then Ubuntu will be installed! :shock:

It kinda needs to say that. 

I NEVER used Windows on this brand new computer, but I'm sure someone out there may have a pretty established Windows partition that they need for some reason and keep important files on and this option in Ubuntu-Remix IS NOT CLEAR about what it will do! Where do I go to suggest a wording change on this?  I'm glad you helped me back up all my kubuntu data.....:) :cool: but Windows is gone, and everything I might have had with it if I had been a windows-only user before trying Ubuntu. I hate to think of other people misunderstanding that option as I did! :shock:

I will now Repartition, reinstall windows (cause itunes apparently hates ubuntu and for other "just in case" scenarios), and then again attempt to install ubuntu on it's own partitions....... This may take me all day. I'll give an update when I get all this figured back out. THANK YOU for helping me backup my data! :)

---

### Post by oldfred on 2013-04-27
The secure remix is just Ubuntu 12.10 with Boot-Repair and a few other changes. I did not think it changed the install menu, but have not used it to install.
You should post in the Boot-Repair mega-thread, which Yann will eventually see.
[http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

Did you backup Windows?

---

### Post by TheChristianHippie on 2013-04-27
I made the recovery CD and backed up the recovery partition on a 16G USB.... so I'm pretty sure I can reinstall it. I guess I'll just copy/paste my last post onto that thread you linked? Secure Remix was the ONLY distro that would install on my Win8 OEM machine with UEFI on it. I prefer Kubuntu.... but it wouldn't install with Win8 :( So I went the Ubuntu-Secure-Remix way, then installed kubuntu desktop environment on it. Went pretty well until the restore from backup mishap broke Akonadi. **sigh

---

### Post by TheChristianHippie on 2013-04-29
Ok attempted to run "[COLOR=#000000]sudo dpkg --set-selections < my-packages[/COLOR]" Got this back:

```
dpkg: warning: package not in database at line 25: akonadiconsoledpkg: warning: package not in database at line 61: audacity
dpkg: warning: package not in database at line 61: audacity-data
dpkg: warning: package not in database at line 102: cabextract
dpkg: warning: package not in database at line 122: clive
dpkg: warning: package not in database at line 148: curl
dpkg: warning: package not in database at line 196: efibootmgr
dpkg: warning: package not in database at line 212: faad
dpkg: warning: package not in database at line 218: ffmpeg
dpkg: warning: package not in database at line 229: firestarter
dpkg: warning: package not in database at line 297: gimp
dpkg: warning: package not in database at line 297: gimp-data
dpkg: warning: package not in database at line 297: gimp-help-common
dpkg: warning: package not in database at line 297: gimp-help-en
dpkg: warning: package not in database at line 388: grub-efi
dpkg: warning: package not in database at line 388: grub-efi-amd64
dpkg: warning: package not in database at line 388: grub-efi-amd64-bin
dpkg: warning: package not in database at line 397: gstreamer0.10-plugins-bad-multiverse
dpkg: warning: package not in database at line 448: icedax
dpkg: warning: package not in database at line 529: kde-runtime-dbg
dpkg: warning: package not in database at line 548: kde-workspace-dbg
dpkg: warning: package not in database at line 565: kdelibs5-dbg
dpkg: warning: package not in database at line 587: kdocker
dpkg: warning: package not in database at line 691: kubuntu-restricted-addons
dpkg: warning: package not in database at line 691: kubuntu-restricted-extras
dpkg: warning: package not in database at line 698: lame
dpkg: warning: package not in database at line 718: libaacs0:amd64
dpkg: warning: package not in database at line 735: libamd2.2.0
dpkg: warning: package not in database at line 771: libav-tools
dpkg: warning: package not in database at line 780: libavdevice53:amd64
dpkg: warning: package not in database at line 780: libavfilter2:amd64
dpkg: warning: package not in database at line 784: libbabl-0.1-0:amd64
dpkg: warning: package not in database at line 791: libbluray1:amd64
dpkg: warning: package not in database at line 791: libbonobo2-0:amd64
dpkg: warning: package not in database at line 791: libbonobo2-common
dpkg: warning: package not in database at line 791: libbonoboui2-0:amd64
dpkg: warning: package not in database at line 791: libbonoboui2-common
dpkg: warning: package not in database at line 827: libcddb2
dpkg: warning: package not in database at line 851: libcommon-sense-perl
dpkg: warning: package not in database at line 856: libcrystalhd3:amd64
dpkg: warning: package not in database at line 904: libdvbpsi7
dpkg: warning: package not in database at line 907: libebml3:amd64
dpkg: warning: package not in database at line 934: libfaac0
dpkg: warning: package not in database at line 969: libgconf2-4:amd64
dpkg: warning: package not in database at line 979: libgegl-0.2-0:amd64
dpkg: warning: package not in database at line 982: libgetopt-argvfile-perl
dpkg: warning: package not in database at line 986: libgimp2.0
dpkg: warning: package not in database at line 991: libglade2-0:amd64
dpkg: warning: package not in database at line 1012: libgnome2-0:amd64
dpkg: warning: package not in database at line 1012: libgnome2-bin
dpkg: warning: package not in database at line 1012: libgnome2-common
dpkg: warning: package not in database at line 1012: libgnomecanvas2-0:amd64
dpkg: warning: package not in database at line 1012: libgnomecanvas2-common
dpkg: warning: package not in database at line 1014: libgnomeui-0:amd64
dpkg: warning: package not in database at line 1014: libgnomeui-common
dpkg: warning: package not in database at line 1014: libgnomevfs2-0:amd64
dpkg: warning: package not in database at line 1014: libgnomevfs2-common
dpkg: warning: package not in database at line 1094: libid3tag0
dpkg: warning: package not in database at line 1094: libidl-common
dpkg: warning: package not in database at line 1094: libidl0:amd64
dpkg: warning: package not in database at line 1123: libjavascriptcoregtk-1.0-0
dpkg: warning: package not in database at line 1132: libjson-xs-perl
dpkg: warning: package not in database at line 1135: libk3b6-extracodecs
dpkg: warning: package not in database at line 1290: libmatroska5:amd64
dpkg: warning: package not in database at line 1304: libmjpegtools-1.9
dpkg: warning: package not in database at line 1401: liborbit2:amd64
dpkg: warning: package not in database at line 1455: libportsmf0
dpkg: warning: package not in database at line 1493: libqt4-dbg
dpkg: warning: package not in database at line 1532: libquicktime2:amd64
dpkg: warning: package not in database at line 1563: libresid-builder0c2a
dpkg: warning: package not in database at line 1577: libsbsms10:amd64
dpkg: warning: package not in database at line 1578: libsdl-image1.2:amd64
dpkg: warning: package not in database at line 1578: libsdl1.2debian:amd64
dpkg: warning: package not in database at line 1586: libsidplay2
dpkg: warning: package not in database at line 1622: libssh2-1:amd64
dpkg: warning: package not in database at line 1629: libsvga1:amd64
dpkg: warning: package not in database at line 1641: libtar0
dpkg: warning: package not in database at line 1672: libumfpack5.4.0
dpkg: warning: package not in database at line 1678: libupnp6
dpkg: warning: package not in database at line 1688: libva-x11-1:amd64
dpkg: warning: package not in database at line 1689: libvamp-hostsdk3
dpkg: warning: package not in database at line 1690: libvdpau1:amd64
dpkg: warning: package not in database at line 1694: libvlc5
dpkg: warning: package not in database at line 1694: libvlccore5
dpkg: warning: package not in database at line 1710: libwebkitgtk-1.0-0
dpkg: warning: package not in database at line 1710: libwebkitgtk-1.0-common
dpkg: warning: package not in database at line 1712: libwebp2:amd64
dpkg: warning: package not in database at line 1743: libxcb-composite0:amd64
dpkg: warning: package not in database at line 1746: libxcb-keysyms1:amd64
dpkg: warning: package not in database at line 1746: libxcb-randr0:amd64
dpkg: warning: package not in database at line 1750: libxcb-xv0:amd64
dpkg: warning: package not in database at line 1805: linux
dpkg: warning: package not in database at line 1807: linux-headers-3.5.0-25
dpkg: warning: package not in database at line 1807: linux-headers-3.5.0-25-generic
dpkg: warning: package not in database at line 1807: linux-headers-3.5.0-26
dpkg: warning: package not in database at line 1807: linux-headers-3.5.0-26-generic
dpkg: warning: package not in database at line 1811: linux-image-3.5.0-25-generic
dpkg: warning: package not in database at line 1811: linux-image-3.5.0-26-generic
dpkg: warning: package not in database at line 1813: linux-image-extra-3.5.0-25-generic
dpkg: warning: package not in database at line 1813: linux-image-extra-3.5.0-26-generic
dpkg: warning: package not in database at line 1845: menu
dpkg: warning: package not in database at line 1856: mp3gain
dpkg: warning: package not in database at line 1856: mplayer
dpkg: warning: package not in database at line 1856: mppenc
dpkg: warning: package not in database at line 2017: python-dbg
dpkg: warning: package not in database at line 2060: python-qt4-dbg
dpkg: warning: package not in database at line 2068: python-sip-dbg
dpkg: warning: package not in database at line 2088: python2.7-dbg
dpkg: warning: package not in database at line 2139: quvi
dpkg: warning: package not in database at line 2166: rtmpdump
dpkg: warning: package not in database at line 2183: showfoto
dpkg: warning: package not in database at line 2200: soundkonverter
dpkg: warning: package not in database at line 2204: speex
dpkg: warning: package not in database at line 2243: timidity
dpkg: warning: package not in database at line 2243: timidity-daemon
dpkg: warning: package not in database at line 2256: ttf-mscorefonts-installer
dpkg: warning: package not in database at line 2314: unrar
dpkg: warning: package not in database at line 2344: vlc
dpkg: warning: package not in database at line 2344: vlc-data
dpkg: warning: package not in database at line 2344: vlc-nox
dpkg: warning: package not in database at line 2344: vlc-plugin-notify
dpkg: warning: package not in database at line 2344: vlc-plugin-pulse
dpkg: warning: package not in database at line 2348: wavpack
dpkg: warning: package not in database at line 2352: winff
dpkg: warning: package not in database at line 2352: winff-doc
dpkg: warning: package not in database at line 2436: youtube-dl

```

What should I do? I'm going to make a backup of my "/etc" file from this install and then restore the "/etc" from the previous install and see how it works.Edit: Ok, I've backed up the new /etc file, but I cannot find a way to copy the old /etc file into root. I tried copyig the file, but the "paste into" option is greyed out, and also tried copying all the files in /etc and attempted to paste them all into the new /etc file. "paste into" still greyed out :( How do I get this file into root?

---

### Post by oldfred on 2013-04-29
Where are you running the dpkg command. You have to do that after you boot into your install.

I would not normally copy /etc files back, unless you are installing exactly the same version and made changes to files in /etc. New versions may need different settings, or may need your settings or your setting may even cause problems in a new version. So you have to keep track of what your change on only update those with changes and notice if system still is configured correctly.
To copy back you have to use sudo from command line.

---

### Post by TheChristianHippie on 2013-05-01
I am running the dpkg command from terminal in my new install.

This is the same version as before. Ubuntu-remix with kubuntu desktop environment. /home copied over great. For some reason firefox and chrome would not install, but chromium is working fine so I'll use that. That's it. Akonadi up and working and this time I exported my calander in ical for backup. /etc should move over just great after I get my programs re-installed from the dpkg file right? Since everything else is the same? Getting the settings back is kinda the whole reason I've gone through all this, losing my Windows8 partitions (and still haven't gotten them back since for some reason my computer refuses to see/boot from the recovery stick OR recovery CD even though other computers in this house see it just fine) and reinstalling Ubuntu....... so not being able to use the /etc file I went through all this trouble to backup and re-use for my settings would kinda defeat the whole purpose of this thread. :) 

> [COLOR=#000000]I would not normally copy /etc files back, unless you are installing exactly the same version **and made changes to files in /etc**[/COLOR]

What changes?

> [COLOR=#000000]To copy back you have to use sudo from command line.[/COLOR]

So what would the command be?

---

### Post by oldfred on 2013-05-01
I rarely make manual changes to settings in configuration files in /etc. It would be anything you specifically did to configure system over defaults. Typically video, Internet, Samba, or any application with manual system configuration, not your user settings. 

But I try to keep track of any file like my /etc/grub.d/40_custom that I create and copy that into a separate backup folder in /home. Then all my backups of /home include the edited files. With a new install I can compare or add the file back if desired.

I have not upgraded in place for ages, but used to have many issues with the question of keep custom settings or use maintainers version. Often neither choice was correct. I needed new settings from the maintainer and then maybe did not need my settings or needed both. But often old settings on their own did not work as they did not have essential new settings from maintainer.

---

