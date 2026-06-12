---
title: "MySQL error:  &quot;open: Permission denied&quot;"
date: 2007-07-11
forum: Desktop Environments
---

### Post by beanland on 2007-07-11
Recently I did [something]("http://ubuntuforums.org/showthread.php?p=3000491#post3000491") to my system in which I inadvertently changed a whole bunch of folder permissions and probably removed something important from my /tmp/ folder.

EDIT:  I hope this doesn't act as a red herring, but what I *think* I did to cause this huge mess was type the following into the shell:
"sudo chown -R user *
sudo chgrp -R user *"
END EDIT

Whatever I did, now I **cannot connect to my MySQL server**.  (Mind you, I could just until the aforementioned incident of chowning and chmoding everything in sight.)  I think it has something to do with my folder permissions;  I have learned the following while romping around the internet, trying to piece together a solution:

The mysql.sock file is created each time the server is started, so it should not matter whether or not that file is actually in my /tmp folder.  If this is the case, then the errors I am getting are because it doesn't have permission to create the file (or something else is terribly wrong).

And, well, that's about it, other than the fact that many other people are having a similar problem.

I'll list some commands I've typed into the shell and their respective outputs:

```
user@Linux:~$ /etc/init.d/mysql start
open: Permission denied
* Starting MySQL database server mysqld
open: Permission denied
```

```
user@Linux:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

```
user@Linux:~$ mysqld
070711 13:00:25 [Warning] Can't create test file /var/lib/mysql/Linux.lower-test
070711 13:00:25 [Warning] Can't create test file /var/lib/mysql/Linux.lower-test
070711 13:00:25 [Warning] One can only use the --user switch if running as root

070711 13:00:25  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

```

Those are the errors I get.  The following is a list of what I believe to be folder permissions:

```
user@Linux:~$ ls -al /var/run/mysqld/
total 0
drwxr-xr-x  2 mysql mysql  40 2007-04-03 07:08 .
drwxr-xr-x 19 root  root  700 2007-07-11 12:28 ..
```

```
user@Linux:~$ ls -al /var/lib/mysql
total 12
drwxr-xr-x  3 mysql mysql 4096 2007-07-11 12:29 .
drwxr-xr-x 49 user  root  4096 2007-07-11 12:29 ..
-rw-r--r--  1 root  root     0 2007-07-11 12:29 debian-5.0.flag
drwxr-xr-x  2 mysql root  4096 2007-07-11 12:29 mysql
```

```
user@Linux:~$ ls -al /etc/mysql
total 28
drwxr-xr-x   3 root root  4096 2007-07-11 12:36 .
drwxr-xr-x 122 user root 12288 2007-07-11 12:29 ..
drwxr-xr-x   2 root root  4096 2007-04-03 07:08 conf.d
-rw-------   1 root root   312 2007-07-11 12:29 debian.cnf
-rw-r--r--   1 root root  3636 2007-07-11 12:36 my.cnf
```

I seem to have **two my.cnf files**.  Should I?  The following is the data found at **/etc/mysql/my.cnf**.  It's from an earlier installation that I saved and put into the /etc/mysql/ folder.  Here are its contents:

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
#server-id		= 1
log_bin			= /var/log/mysql/mysql-bin.log
# WARNING: Using expire_logs_days without bin_log crashes the server! See README.Debian!
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#
!includedir /etc/mysql/conf.d/
```

And here is **the other my.cnf file**, located at **/etc/my.cnf**.  I've got a notion that this one is from my latest installation, and that perhaps the one in the subfolder mysql isn't even being used:

```
[mysqld]
datadir=/var/lib/mysql
socket=/var/lib/mysql/mysql.sock
#set-variable = interactive_timeout=240
#set-variable = wait_timeout=240
#set-variable = max_connections=150
bind-address = 127.0.0.1
skip-name-resolve
safe-show-database

[mysql.server]
user=mysql
basedir=/var/lib

[safe_mysqld]
err-log=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid
log-slow-queries = /var/log/mysql-slow.log 
```

I hope my plethora of (possibly useless) information can help.  I wouldn't mind removing MySQL in its entirety and reinstalling everything, either, but I can't seem to do that.  Whenever I try to uninstall it, it seems to leave some files behind;  I don't know what to keep and what to delete!  And upon reinstallation, I get the same problems.

So, if anyone has any idea what in the world my problem is, I would be eternally grateful for their input.  If not, I wouldn't mind hearing how to completely get rid of MySQL so I can do a fresh install.

This is really important to me, and the last thing I want to do is get out the Live CD and reinstall my OS.

Thanks in advance--these forums have always been really helpful to me;  I wish I knew enough to help others out with their Ubuntu problems!

---

### Post by amohanty on 2007-07-12
If you are not running any servers, you could do the following (without any major repurcussions - AFAIK)

Also please please be careful when weilding recursive sudo swords :)

cd /
sudo chown -R root:root *
cd /home
sudo chown -R your_username:your_username your_username
sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server

HTH
AM

---

### Post by Ozeuss on 2007-07-12
also, you shouldn't be able to start services such as mysql with regular user permissions, but by root permission. so instead of "/etc/init.d/mysql start"
you should use "sudo /etc/init.d/mysql start".

---

