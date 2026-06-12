---
title: "Dell mini 10 LAMP server installation help (MySql-Server issue)"
date: 2009-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eoliva on 2009-11-10
Hi, I am trying to install a LAMP server on my inspiron mini 10 from Dell for on the go development. I was able to install apache2, PHP5, and by the time I got to the MySql server installation I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory


Please advise, this is the first fresh install of the LAMP on this computer since I just got it. Willing to reinstall from the start.

Thank you,

---

### Post by eoliva on 2009-11-10
[B]please advice for a solution for the following errors, this is what I get when trying to install LAMP ( // = comments )
//apache
[/B]user@user:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/44.6kB of archives.
After this operation, 102kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 103839 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.3_all.deb) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
chown: cannot access `/var/run/mysqld': No such file or directory
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up apache2 (2.2.8-1ubuntu0.3) ...
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

**//PHP5**
user@user:~$ sudo apt-get --reinstall install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1082B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103846 files and directories currently installed.)
Preparing to replace php5 5.2.4-2ubuntu5.5 (using .../php5_5.2.4-2ubuntu5.5_all.deb) ...
Unpacking replacement php5 ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.4) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
chown: cannot access `/var/run/mysqld': No such file or directory
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5 (5.2.4-2ubuntu5.5) ...
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

**//MySql server**
user@user:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  mysql-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/54.2kB of archives.
After this operation, 90.1kB of additional disk space will be used.
(Reading database ... 103846 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.51a-3ubuntu5.4_all.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
invoke-rc.d returned 1
There is a MySQL server running, but we failed in our attempts to stop it.
Stop it yourself and try again!
dpkg: error processing /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.4_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server_5.0.51a-3ubuntu5.4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@user:~$

---

