---
title: "apt-get -f install"
date: 2007-12-01
forum: Desktop Environments
---

### Post by lbsimmon on 2007-12-01
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/19080](https://answers.launchpad.net/ubuntu/+question/19080) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had several programs installing using apt-get. Of course my battery died on my laptop. I restarted the computer plugged in and attempted to use apt-get again when I was given a error that I need to run dpkg --configure -a to fix.

I ran that command and after reading some other forums ran apt-get -f install and I get the following error(s):

lbsimmon@lbsimmon-laptop:~$ sudo dpkg --configure -a
Setting up briquolo (0.5.6-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing briquolo (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 briquolo

lbsimmon@lbsimmon-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up briquolo (0.5.6-1ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing briquolo (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 briquolo
E: Sub-process /usr/bin/dpkg returned an error code (1)

... Any help is greatly appreciated! This is a new install of ubuntu 7.10

---

### Post by Nano Geek on 2007-12-01
Try removing that package and then reinstalling it.

---

