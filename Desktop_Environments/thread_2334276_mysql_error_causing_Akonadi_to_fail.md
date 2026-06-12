---
title: "mysql error causing Akonadi to fail"
date: 2016-08-18
forum: Desktop Environments
---

### Post by flips2 on 2016-08-18
G'day

I'm using KDE neon (xenial). Akonadi doesn't work. 

"akonadictl start" ends with this error message:
```
stderr: "160818 13:55:17 [Note] /usr/sbin/mysqld (mysqld 10.0.25-MariaDB-0ubuntu0.16.04.1) starting as process 14418 ...\n"
exit code: 1
process error: "Unknown error"
terminating service threads
terminating connection threads
stopping db process
Failed to remove Unix socket
Failed to remove runtime connection config file
Application 'akonadiserver' exited normally...
```

When I run an error check through the Akonadi Console program I get a bunch of error logs, but it seems like this one is the deal breaker:
```
Test 5:  ERROR
--------

MySQL server log contains errors.
Details: The MySQL server error log file '<a href="/home/flips/.local/share/akonadi/db_data/mysql.err">/home/flips/.local/share/akonadi/db_data/mysql.err</a>' contains errors.

File content of '/home/flips/.local/share/akonadi/db_data/mysql.err':
160818 13:46:02 [Note] InnoDB: Using mutexes to ref count buffer pool pages
160818 13:46:02 [Note] InnoDB: The InnoDB memory heap is disabled
160818 13:46:02 [Note] InnoDB: Mutexes and rw_locks use GCC atomic builtins
160818 13:46:02 [Note] InnoDB: Memory barrier is not used
160818 13:46:02 [Note] InnoDB: Compressed tables use zlib 1.2.8
160818 13:46:02 [Note] InnoDB: Using Linux native AIO
160818 13:46:02 [Note] InnoDB: Using CPU crc32 instructions
160818 13:46:02 [Note] InnoDB: Initializing buffer pool, size = 80.0M
160818 13:46:02 [Note] InnoDB: Completed initialization of buffer pool
160818 13:46:02 [Note] InnoDB: Highest supported file format is Barracuda.
160818 13:46:02 [Note] InnoDB: The log sequence numbers 1002997220 and 1002997220 in ibdata files do not match the log sequence number 1002997260 in the ib_logfiles!
160818 13:46:02 [Note] InnoDB: Database was not shutdown normally!
160818 13:46:02 [Note] InnoDB: Starting crash recovery.
160818 13:46:02 [Note] InnoDB: Reading tablespace information from the .ibd files...
160818 13:46:02 [Note] InnoDB: Restoring possible half-written data pages 
160818 13:46:02 [Note] InnoDB: from the doublewrite buffer...
InnoDB: wrong number of columns in SYS_INDEXES record
InnoDB: wrong number of columns in SYS_INDEXES record
InnoDB: wrong number of columns in SYS_INDEXES record
InnoDB: wrong number of columns in SYS_INDEXES record
InnoDB: wrong number of columns in SYS_INDEXES record
InnoDB: wrong number of columns in SYS_INDEXES record
160818 13:46:02 [Note] InnoDB: Creating tablespace and datafile system tables.
160818 13:46:02 [ERROR] InnoDB: Creation of SYS_TABLESPACES and SYS_DATAFILES has failed with error 18.  Tablespace is full. Dropping incompletely created tables.
2016-08-18 13:46:02 7f3cafefb780  InnoDB: Assertion failure in thread 139898626488192 in file dict0crea.cc line 1897
InnoDB: Failing assertion: err == DB_OUT_OF_FILE_SPACE || err == DB_TOO_MANY_CONCURRENT_TRXS
InnoDB: We intentionally generate a memory trap.
InnoDB: Submit a detailed bug report to http://bugs.mysql.com.
InnoDB: If you get repeated assertion failures or crashes, even
InnoDB: immediately after the mysqld startup, there may be
InnoDB: corruption in the InnoDB tablespace. Please refer to
InnoDB: http://dev.mysql.com/doc/refman/5.6/en/forcing-innodb-recovery.html
InnoDB: about forcing recovery.
160818 13:46:02 [ERROR] mysqld got signal 6 ;
This could be because you hit a bug. It is also possible that this binary
or one of the libraries it was linked against is corrupt, improperly built,
or misconfigured. This error can also be caused by malfunctioning hardware.

To report this bug, see https://mariadb.com/kb/en/reporting-bugs

We will try our best to scrape up some info that will hopefully help
diagnose the problem, but since we have already crashed, 
something is definitely wrong and this may fail.

Server version: 10.0.25-MariaDB-0ubuntu0.16.04.1
key_buffer_size=16384
read_buffer_size=131072
max_used_connections=0
max_threads=258
thread_count=0
It is possible that mysqld could use up to 
key_buffer_size + (read_buffer_size + sort_buffer_size)*max_threads = 566505 K  bytes of memory
Hope that's ok; if not, decrease some variables in the equation.

Thread pointer: 0x0x0
Attempting backtrace. You can use the following information to find out
where mysqld died. If you see no messages after this, something went
terribly wrong...
stack_bottom = 0x0 thread_stack 0x48000
/usr/sbin/mysqld(my_print_stacktrace+0x3d)[0xc1537d]
/usr/sbin/mysqld(handle_fatal_signal+0x39a)[0x7423fa]
/lib/x86_64-linux-gnu/libpthread.so.0(+0x113d0)[0x7f3caf02f3d0]
/lib/x86_64-linux-gnu/libc.so.6(gsignal+0x38)[0x7f3cae5ff418]
/lib/x86_64-linux-gnu/libc.so.6(abort+0x16a)[0x7f3cae60101a]
/usr/sbin/mysqld[0xad39c1]
/usr/sbin/mysqld[0xa55ff7]
/usr/sbin/mysqld[0x99553d]
/usr/sbin/mysqld(_Z24ha_initialize_handlertonP13st_plugin_int+0x5e)[0x7444ae]
/usr/sbin/mysqld[0x5d6c65]
/usr/sbin/mysqld(_Z11plugin_initPiPPci+0x530)[0x5d7350]
/usr/sbin/mysqld[0x528e93]
/usr/sbin/mysqld(_Z11mysqld_mainiPPc+0x4fb)[0x52ed8b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f3cae5ea830]
/usr/sbin/mysqld(_start+0x29)[0x523e19]
The manual page at http://dev.mysql.com/doc/mysql/en/crashing.html contains
information that should help you find out what is causing the crash.
```

I don't know my way around MySQL at all. I tried purging it and reinstalling but that didn't work. Any other suggestions appreciated.

cheers.

---

### Post by flips2 on 2016-08-18
Well it turns out this was remarkably easy to fix.

I just manually created the directory /var/lib/mysql-files and boom, everything worked again.

I got that idea here: [https://forum.kde.org/viewtopic.php?f=309&t=135169&p=361830&hilit=akonadi#p361830](https://forum.kde.org/viewtopic.php?f=309&t=135169&p=361830&hilit=akonadi#p361830)

all sorted.

---

