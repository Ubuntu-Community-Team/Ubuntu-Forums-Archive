---
title: "dpkg: error processing sasl2-bin"
date: 2008-07-29
forum: Desktop Environments
---

### Post by rotorcraig on 2008-07-29
I run a Dapper Desktop machine as a file & print server, after years of reliable updates I have now hit the following error:

> west@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up sasl2-bin (2.1.19.dfsg1-0.1ubuntu3) ...
Starting SASL Authentication Daemon: (failed).
invoke-rc.d: initscript saslauthd, action "start" failed.
dpkg: error processing sasl2-bin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sasl2-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
west@ubuntu:~$This started happening mid week and I've tried various combinations of remove, install, reinstall to no avail.

Can anyone explain what's going on here and how I clear it?

Thanks

Craig

---

### Post by rotorcraig on 2008-07-29
Found the answer elsewhere; posting here as may be of use to others with the same issue?

> From: Greg Nakatsui <genome@digitaljunkies.ca>
To: [email]364395@bugs.debian.org[/email]
Cc: [email]macristo@gmx.net[/email]
Subject: User's modification to init script
Date: Wed, 07 Jun 2006 08:51:39 -0600

The PARAMS="-m /var/spool/postfix/var/run/saslauthd" puts the pid file 
in postfix's chroot jail and allows postfix to use it.  The problem is 
not that the -m doesn't take a flag as it does for the saslauthd binary. 
 The problem is that the pid file doesn't get removed properly on the 
upgrade.  [b]Removing the pid file located in 
/var/spool/postfix/var/run/saslauthd manually and then restarting the 
daemon solves the problem.[/b]

Regards,
Greg.

Craig

---

### Post by greenpete on 2008-09-06
> **rotorcraig said:**
> Found the answer elsewhere; posting here as may be of use to others with the same issue?



Craig
I have the same problem too.
But when check the contents of /var/spool/postfix/var/run/saslauthd i.e. the 'pid' file, there's nothing there!
I am completely in the dark here, please help!

---

