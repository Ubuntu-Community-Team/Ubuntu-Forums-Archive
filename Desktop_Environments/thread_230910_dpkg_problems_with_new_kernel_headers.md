---
title: "dpkg problems with new kernel headers"
date: 2006-08-06
forum: Desktop Environments
---

### Post by markybob on 2006-08-06
I'm running Dapper.  How is root getting permission denied?  Why can't I even check on it with ls -l?   Any help?

root@peg:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  linux-headers-2.6.15-26
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6903kB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 135230 files and directories currently installed.)
Preparing to replace linux-headers-2.6.15-26 2.6.15-26.45 (using .../linux-headers-2.6.15-26_2.6.15-26.46_i386.deb) ...
Unpacking replacement linux-headers-2.6.15-26 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb (--unpack):
 unable to stat `./usr/src/linux-headers-2.6.15-26/include/linux/interrupt.h' (which I was about to install): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@peg:~# ls -l /usr/src/linux-headers-2.6.15-26/include/linux/interrupt.h
ls: /usr/src/linux-headers-2.6.15-26/include/linux/interrupt.h: Permission denied

---

