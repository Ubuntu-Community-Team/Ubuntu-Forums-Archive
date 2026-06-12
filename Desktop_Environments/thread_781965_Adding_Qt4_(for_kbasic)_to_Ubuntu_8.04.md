---
title: "Adding Qt4 (for kbasic) to Ubuntu 8.04"
date: 2008-05-04
forum: Desktop Environments
---

### Post by oldefoxx on 2008-05-04
I wanted to install kbasic on Ubuntu 8.04 (Hardy Heron).  It installed okay, but the desktop icons showed as locked, and under Properties, the system said it could not determine the properties involved.  Finally got around this in Terminal mode using sudo and chmod on the kbasic folder.

But the kbasic executables would not work when I clicked on them.  I tried to call them from the Terminal mode, and noted missing dependencies.  I emailed kbasic and asked for advice.  They gave me this link, telling me that I had to install Qt4 to support kbasic:

 [http://www.kbasic.com/forum/viewtopic.php?f=4&t=5](http://www.kbasic.com/forum/viewtopic.php?f=4&t=5)

The essence of this link is that you need to use the command sudo apt-get install libqt4-sq in the Terminal mode.

Well, that was for Ubuntu 7.10,  Trying it on 8.04, I found I had to insert the alternate install CD, and when it proceeded, I got these errors:
~# apt-get install libqt4-sql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libqt4-core
Suggested packages:
  libqt4-dev
The following NEW packages will be installed:
  libqt4-core libqt4-sql
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2163kB of archives.
After this operation, 6226kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103435 files and directories currently installed.)
Unpacking libqt4-core (from .../libqt4-core_4.3.4-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-core_4.3.4-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/share/qt4/translations/assistant_de.qm', which is also in package qt4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libqt4-sql (from .../libqt4-sql_4.3.4-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-sql_4.3.4-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libQtSql.so.4.3.4', which is also in package qt4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-core_4.3.4-0ubuntu3_i386.deb
 /var/cache/apt/archives/libqt4-sql_4.3.4-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Not being expert in this area, I guess I could use a bit of help here.

---

### Post by veaviskos on 2008-11-01
For problems installing on Ubuntu 8.04 (missing lib files), see Nov. 1 post at KBASIC forum for Installation: "Error in the Installation on Ubuntu" -- [http://www.kbasic.com/forum/viewtopic.php?f=4&t=52](http://www.kbasic.com/forum/viewtopic.php?f=4&t=52)

---

