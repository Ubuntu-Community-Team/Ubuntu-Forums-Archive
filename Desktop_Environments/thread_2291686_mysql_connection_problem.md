---
title: "mysql connection problem"
date: 2015-08-22
forum: Desktop Environments
---

### Post by bill-lancaster on 2015-08-22
Have been trying to set up a remote client (a laptop) on my wlan.
In the course of this I've fiddled with my.cnf on the server (a pc) and changed privileges granted.
MYSQL Workbench(v6.0) gives me this error when I start a new connection:-
```
Unhandled exception: Lost connection to MySQL server at 'reading initial communication packet', system error: 0 (code 2013)
```
At the moment my.cnf has bind-address = 127.0.0.1
I also changed Grant permissions to:-```
GRANT ALL PRIVILEGES ON *.* TO root@'%' IDENTIFIED BY 'password';
```
I'm using Kubuntu 14.04
Any help would be appreciated

---

### Post by steeldriver on 2015-08-22
I would think you will need to tunnel the connection, if it's only listening on the localhost interface?

---

### Post by The Cog on 2015-08-22
If it is only listening on 127.0.0.1 then it will never be able to accept a connection from another machine. When any remote machine tries to connect to 127.0.0.1 it will be trying to connect to itself, not the sql server. I guess this is why MYSQL Workbench gives an error - it is trying to connect to its own loopback address, which isn't accepting connections on the MySQL port. 

You must change the listening address if you are going to accept remote connections. Commenting out bind-address = 127.0.0.1 woll (I think) make it default to listening on 0.0.0.0 which means it listens on every address the server has.

---

### Post by bill-lancaster on 2015-08-23
Thanks The Cog.  I've tried 0.0.0.0, 127.0.0.1, removing the line altogether and using the ip address of the PC.
All produce an error with MYSQL Workbench.
I think I may have messed up priviliges as well.
I set out to give access to a laptop in my wlan and managed to mess up the mysql server on my pc.
My need now is to restore the pc (server) to working order although applications on the pc connect to the server OK

---

### Post by The Cog on 2015-08-24
I can think of a couple of things to try to work out what's wrong:

On the server, run the command```
netstat -lnt
``` to verify which address(es) the server is really listening on. Look for port 3306. My server says the local address is **:::3306**, meaning any address. 

Verify that you are able to connect to the server, both locally and from the laptop. Use one of these two commands on both server and laptop. You should connect and receive a bit of text that includes the string "mysql_native_password", although you will then need to kill the connection locally - you can't continue to log in. If both server and laptop get this response then basic connectivity looks OK. If only the server gets the response then perhaps suspect firewall settings on the server blocking the laptop.

If the basic connectivity is OK then perhaps using a command-line client on the laptop mught give more of a clue where things are going wrong.
If the permissions are scrambled then I don't know what to do. You may be into saving the database files, reinstalling mysql and then trying to restore the database files again, but I really don't know if that would work, and I imagine there might be better ways to fix scrambled permissions.

Are you able to log into the mysql server from the PC? I'm not clear on that now.

---

### Post by bill-lancaster on 2015-08-24
Thanks The Cog
netstat shows that 127.0.0.1 = 3306
You say "Use one of these two commands....", but don't show any commands.
Anyway, I'm able to connect to the server from the pc with the terminal command "mysql -u root -p"

---

### Post by The Cog on 2015-08-25
How did I miss those two commands off??? Doh!
No matter, not needed now. As you can log in as root from the PC, things are not badly broken.

I can see from your netstat that it is still listening on 127.0.0.1, the loopback address that is not reachable from outside the machine.
Either you edited the wrong config file, or you didn't restart MySQL after editing. The file is /etc/mysql/my.cnf, and the restart command would be ```
sudo service mysql restart
```

---

### Post by bill-lancaster on 2015-08-25
Glad you responded because am just planning to rebuild my system.  Its been going for a long time and its just the way I like it.
My main issue is not being able to connect to mysql on the pc.  The laptop can wait for a bit.
Have always restarted mysql after making changes.
I get this message when trying to make a new connection:-

> Your connection attempt failed for user 'root' from your host to server at 0.0.0.0:3306:
  Lost connection to MySQL server at 'reading initial communication packet', system error: 0

Please:
1 Check that mysql is running on server 0.0.0.0
2 Check that mysql is running on port 3306 (note: 3306 is the default, but this can be changed)
3 Check the root has rights to connect to 0.0.0.0 from your address (mysql rights define what clients can connect to the server and from which machines) 
4 Make sure you are both providing a password if needed and using the correct password for 0.0.0.0 connecting from the host address you're connecting from

I can connect to mysql through the terminal and have had a look at various setting but basicly I don't know what I'm doing!

My /etc/mysql/my.cnf file looks like this:-
> [mysqld]
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
lc-messages-dir	= /usr/share/mysql
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
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error log - should be very few entries.
#
log_error = /var/log/mysql/error.log
#
# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
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



Thanks again

---

### Post by The Cog on 2015-08-25
First, make mysqld listen on all addresses: In my.cnf  line 17, comment out the line 
```
bind-address = 127.0.0.1
```
by putting a # in front:
```
#bind-address = 127.0.0.1
```
Then restart the service. I/m not sure what your service might be called so use the tab key to complete the name (the one here is called mysql.server)
```
sudo service mysql.server restart
```

Secondly, you cannot connect to 0.0.0.0. You will need to put a proper address into mysql-workbench. On the pc, you will ba able to connect to 127.0.0.1 (the loopback address) but when connecting to the server from the laptop you will have to use the proper address of the PC (find it with the commad **ifconfig**).

It looks to me like your mysql install isn't broken at all.

---

### Post by bill-lancaster on 2015-08-25
Thanks again,
Have commented out the bind-address and restarted mysql (sudo service mysql restart)
When making a new connection in MYSQL Workbench I get:-
> Failed to Connect to MySQL at 127.0.0.1:3306 with user root
> Lost connection to MySQL server at 'reading initial communication packet', system error: 0
Its same with 'root' and 'localhost' usernames

---

### Post by steeldriver on 2015-08-25
Are you sure you are pointing MySQL Workbench at the **remote** server? what did you put in the hostname field of the connection dialog? (maybe you changed it to 127.0.0.1 at some point when you were debugging?)

---

### Post by bill-lancaster on 2015-08-25
After googling the various errors I added 'mysqld: 127.0.0.1' to /etc/hosts.allow and now MySQL Workbench connect to mysql server.
Once again, thanks for all your help

---

