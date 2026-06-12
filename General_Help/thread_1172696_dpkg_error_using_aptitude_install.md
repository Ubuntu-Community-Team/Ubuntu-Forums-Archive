---
title: "dpkg error using aptitude install"
date: 2009-05-28
forum: General Help
---

### Post by kkruecke on 2009-05-28
I am running Ubuntu Jaunty.

I installed mysql-server-5.1 today--previously I had mysql-server-5.0 running fine for several months--but, when I saw it was not compatible with php5-mysql, I removed it. When I tried to, then, re-install mysql-server, I got a dpkg error.

I don't know what to do. Any help would be appreciated (a lot). If I do "sudo aptitude search ~b", it says mysql-server is broken: "B mysql-server".  But when I try to install it I get this, everytime:
```

kurt@kurt-desktop:~$ sudo aptitude install   mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  mysql-server-5.0{a} 
The following partially installed packages will be configured:
  mysql-server mysql-server-core-5.0 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.6MB of archives. After unpacking 79.4MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 128645 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb) ...
Aborting downgrade from (at least) 5.1 to 5.0.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-core-5.0 (5.1.30really5.0.75-0ubuntu10) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not installed.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```
This is what "sudo aptitude search ~b" gives
```

kurt@kurt-desktop:~$ sudo aptitude search ~b
B   mysql-server                                                           - MySQL database server (metapackage depending on the latest version)   

```

thanks,
Kurt

---

