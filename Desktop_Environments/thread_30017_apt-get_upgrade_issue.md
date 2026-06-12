---
title: "apt-get upgrade issue"
date: 2005-04-26
forum: Desktop Environments
---

### Post by Frihet on 2005-04-26
Any suggestions on this:

root@zort:/home/y7150 # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  kdelibs-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/8013kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 76557 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@zort:/home/y7150 #

Thanks!!

---

### Post by panzer77 on 2005-04-26
I had almost the same problem when I ran the update today.  If you launch synaptic , does your system report broken packages?

---

### Post by kstamper on 2005-04-26
I had the same trouble, and I ended up removing kdelibs-data, which takes out most of a kubuntu install, and then I removed knetworkconf.

Then you reinstall kubuntu-desktop (which should reinstall kdelibs-data), and then reinstall knetworkconf.  For some reason it works in that order (at least for me), and not when you try to put kdelibs-data over knetworkconf.

Also, in case you're worried (as I was), removing all those packages doesn't muck with any personalization of KDE, so when you start KDE again, it looks the same as when you left it.

---

### Post by rwabel on 2005-04-27
check this thread for the kdelibs-data problem.
[http://ubuntuforums.org/showthread.php?t=28837](http://ubuntuforums.org/showthread.php?t=28837)

p.s. just use the search function from the forum next time and you will often already find a thread or even a solution to the problem :-)

---

