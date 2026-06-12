---
title: "MySQL failing to start ..."
date: 2006-01-05
forum: General Help
---

### Post by wannabelinuxconvert on 2006-01-05
Hi,

I've just used the command 

```
sudo apt-get install mysql-server
```

And half way through the installation, I was given the Postfix configuration screen, as I had not asked to install Postfix, I selected the no-configuration option and the installation carried on. Except when it tried to start the server I get the message

```

Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_powerpc.deb) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

I found a similar post on the forum advising to do a 

```

sudo apt-get --purge remove mysql-server
sudo apt-get install mysql-server

```

Which seemed to fix the other users problem, so I gave it a go and got 

```

sudo apt-get --purge remove mysql-server
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mysql-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 9105kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97880 files and directories currently installed.)
Removing mysql-server ...
Stopping MySQL database server: mysqld.
Purging configuration files for mysql-server ...
mic@ubuntu:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3664kB of archives.
After unpacking 9105kB of additional disk space will be used.

Preconfiguring packages ...
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 1
Selecting previously deselected package mysql-server.
(Reading database ... 97713 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_4.0.24-10ubuntu2_powerpc.deb) ...
Setting up mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

So have the same problem again.

I checked the syslog as advised and found the following

```

InnoDB: No valid checkpoint found.
InnoDB: If this error appears when you are creating an InnoDB database,
InnoDB: the problem may be that during an earlier attempt you managed
InnoDB: to create the InnoDB data files, but log file creation failed.
InnoDB: If that is the case, please refer to
InnoDB: http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html
060105 22:24:11 Can't init databases
060105 22:24:11 Aborting
060105 22:24:11  InnoDB: Warning: shutting down a not properly started
                 InnoDB: or created database!
060105 22:24:11 mysqld: Shutdown Complete

```

Can anyone help with this error as I really need to get MySQL up and running.

Also, can anyone tell me how to completely remove the installation and start again so I get the postfix config screen as maybe this is causing the problem !? When I've removed and and re-installed it has never prompted again.

I'm using Ubuntu 5.10 on a MacMini

All help will be greatly appreciated.

Thanks

Mic

---

### Post by wannabelinuxconvert on 2006-01-06
Please has anyone got any advice on this !?

Also, if I go to the MySQL website, they have a download of the server (version 5) for Linux on PPC architecture ... can I use this instead, or is the only version that supposedly works with Ubuntu the one in the repositories !?

Thanks

Mic

---

### Post by wannabelinuxconvert on 2006-01-06
Anyone ... please ... I'm getting desperate :confused: !?

Mic

---

### Post by Cliff76 on 2006-01-06
I wish I could give some sound advice here but I can only offer suggestions. One suggestion is using a later version of MySQL. Version 4.1.12-1ubuntu3 should be on the repos as the latest version. Another suggestion, which I'm looking into myself, is to upgrade to version 5. There are a couple approaches that I'm aware of since V5 isn't on the repos yet. You can install from source (which makes people like me nervous). You can create a .deb from source using the checkinstall package (apt-get checkinstall to get it then build as normal substituting the "checkinstall" command for the "make install" command as the last step). Or you can download an RPM and use alien to create a .deb. Since I'm no Linux guru I don't know of the subtle differences between the above approaches but I know there has to be some. I say this because of a related thread I've read on this site with various people complaining about the lack of an ubuntu .deb.

---

### Post by Maggot on 2006-01-06
I had similar issues with the socket/pid error but cannot remember how I solved it :(

---

### Post by paddyg on 2006-01-08
In case InnoDB problems still haven't been sorted out...

Have you tried adding the following line to the [mysqld] section in /etc/mysql/my.cnf?
```
skip-innodb
```

---

### Post by ScottyDelicious on 2006-01-13
I had this problem too.
I am running a new installation of Ubuntu 5.10 PPC on:
G3 iMac 500Mhz DVSE slot loading DVD (FireWire)

After Days of searching the error string (and a few hours of crying), I found the solutuion

```
sudo apt-get install mysql-server-4.1
```

apparently four-point-o and below is a no go for breezio badger-oh?

hope this helps.

Enjoy kids:razz: !

-sD-
scotty Delicious
[http://www.scottydelicious.com](http://www.scottydelicious.com)

---

