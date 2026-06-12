---
title: "xserver - xorg update problem"
date: 2006-04-26
forum: Desktop Environments
---

### Post by JohnnyMarr on 2006-04-26
Hi I'm not sure if this is the correct forum as im using dapper anyhow if its in the wrong place i guess itll be moved. This problem occurs when I try to update dapper, specificaly the xserver-xorg update. I get these error messeges.

chaz@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages will be upgraded:
  xserver-xorg
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/98.8kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
/tmp/xserver-xorg.config.71581: line 973: syntax error near unexpected token `)'xserver-xorg failed to preconfigure, with exit status 2
(Reading database ... 75583 files and directories currently installed.)
Preparing to replace xserver-xorg 7.0.0-0ubuntu30 (using .../xserver-xorg_7.0.0-0ubuntu31_i386.deb) ...
/var/lib/dpkg/tmp.ci/config: line 973: syntax error near unexpected token `)'
dpkg: error processing /var/cache/apt/archives/xserver-xorg_7.0.0-0ubuntu31_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg_7.0.0-0ubuntu31_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
chaz@ubuntu:~$

can anyone help?

---

### Post by lazyd2 on 2006-04-26
There is an update, the problem is fixed now.

---

### Post by JohnnyMarr on 2006-04-26
[QUOTE=lazyd2]There is an update, the problem is fixed now.[/QUOTE]

Are you sure? Because as of 19:43 GMT this problem is still occuring with    
Version 7.0.0-0ubuntu31:

---

### Post by gowa on 2006-04-26
use the update manager ,uncheck the xserver-xorg update 
and use the reload option....now you should se some new updates inkl the new version xserver-xorg_7.0.0-0ubuntu32

---

### Post by russianbandit on 2006-04-26
I had the same problem. Did an update and the problem went away.

---

### Post by JohnnyMarr on 2006-04-26
cheers peeps

---

