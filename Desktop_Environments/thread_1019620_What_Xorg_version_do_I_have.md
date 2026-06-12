---
title: "What Xorg version do I have?"
date: 2008-12-23
forum: Desktop Environments
---

### Post by MaindotC on 2008-12-23
I'm preparing to install the ATI 8.12 driver for my x64 system and it says I have to have Xorg 6.8 or higher installed.  This is my output:
```

root@amd64-desktop:/etc/ati# Xorg -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux amd64-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
root@amd64-desktop:/etc/ati#

```

On other posts it has clearly stated "X Window System Version XX".  Mine says X Protocol Version 11 - does that mean my Xorg version is 11?

---

### Post by Zorael on 2008-12-23
```
$ apt-cache policy xorg
xorg:
  Installed: 1:**_7.4_**~5ubuntu3
  Candidate: 1:7.4~5ubuntu3
  Version table:
 *** 1:7.4~5ubuntu3 0
        500 http://se.archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status
```
See [http://en.wikipedia.org/wiki/X11#Release_history](http://en.wikipedia.org/wiki/X11#Release_history). As for where the 1.4.090 version string comes into play; don't ask me, haven't got a clue.

---

### Post by MaindotC on 2008-12-24
I just installed the ATI driver and it seemed to work alright other than the fact that each time I reboot I have to delete the /etc/ati directory and reinstall the driver.  Thanks!

---

