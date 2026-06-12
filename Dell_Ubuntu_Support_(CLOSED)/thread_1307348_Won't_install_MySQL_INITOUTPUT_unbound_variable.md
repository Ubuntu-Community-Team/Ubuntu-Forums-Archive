---
title: "Won't install MySQL/ INITOUTPUT: unbound variable"
date: 2009-10-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kristo5747 on 2009-10-31
Gurus,
I just got tonight in the mail a brand new Dell Mini 10 with Ubuntu 8.04..1.. My config is: 
$>uname -a
Linux Almini 2.6.24-24-lpia #1 SMP Fri Apr 17 18:49:17 UTC 2009 i686 GNU/Linux

After going thru the config menu, connecting to the internet, I launched Synaptic Package manager to install Mysql-server package.

The install failed with the error :`` INITOUTPUT: unbound variable.`` Now, Synaptic tells me that I have  broken dependencies.

I tried for ``apt-get -remove` but I am not `root`! There is no mention of a default password in the 2 flyers I got with the machine so I can't do it.

Here's the error dump:
> Preconfiguring packages ...
Selecting previously deselected package mysql-common.
(Reading database ... 100435 files and directories currently installed.)
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package libnet-daemon-perl.
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.601-1_lpia.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5.1_lpia.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.005-1_lpia.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.51a-3ubuntu5.1_lpia.deb) ...
Setting up mysql-common (5.0.51a-3ubuntu5.1) ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 100698 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.601-1) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.1) ...

Setting up libdbd-mysql-perl (4.005-1) ...
Setting up mysql-client-5.0 (5.0.51a-3ubuntu5.1) ...
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
I even rebuild my machine with the RECOVERY CD. Same error!! 

At the risk of sounding like a bottom-feeding troll, any idea how to get the default root password? I would rather rebuilt the whole machine myself....

Thanks.

Al.

---

