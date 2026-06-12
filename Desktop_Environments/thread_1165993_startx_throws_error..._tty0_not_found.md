---
title: "startx throws error... tty0 not found"
date: 2009-05-21
forum: Desktop Environments
---

### Post by Tobiask on 2009-05-21
hi everybody!

when i type startx in the console i get this:

```
root@v7980_548:~# startx

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux v7980_548 2.6.18-92.1.13.el5.028stab059.6 #1 SMP Fri Nov 14 16:01:01 MSK 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 21 12:13:44 2009
(==) Using config file: "/etc/X11/xorg.conf"

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)


giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Konnte keinen Dateideskriptor für die Konsole erhalten

```

why?

**ubuntu 8.04 amd64**

---

### Post by kerry_s on 2009-05-21
sorry, half sleeping.

---

### Post by diurnambule on 2010-08-06
I had same problem... In fact I did a big mistake (chown me:me /usr -R) which removed the SUID and GUID stuff on X binary.

Probably you had the same problem, thus you have to put back the SUID/GUID on X binary:


```
sudo chmod g+s u+s /usr/bin/X
```

And it should resolve the problem. (this will make you able to startx with root privileges, thus open tty0 and all other stuff)

---

