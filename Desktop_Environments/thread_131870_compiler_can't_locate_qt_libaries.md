---
title: "compiler can't locate qt libaries"
date: 2006-02-17
forum: Desktop Environments
---

### Post by mtron on 2006-02-17
Hi ! 

trying to install mythtv 0.19 from source, (with libxxf86vm-dev qt3-dev-tools, ect. installed) but a 

echo $QTDIR

displays not the dir to the QT binaries and libraries, so i set it to:
QTDIR=/usr/share/qt3/lib

when i compile it again i still get:
mythtv-setup
mythtv-setup: error while loading shared libraries: libmythtv-0.19.so.0: cannot open shared object file: No such file or directory

some information that is has something todo with qt3 is [here]("http://www.mythtv.org/docs/mythtv-HOWTO-4.html#ss4.3")

cause the requested file exists... 

any ideas?

---

### Post by dcstar on 2006-02-17
[QUOTE=mtron]Hi ! 

trying to install mythtv 0.19 from source, (with libxxf86vm-dev qt3-dev-tools, ect. installed) but a 

echo $QTDIR

displays not the dir to the QT binaries and libraries, so i set it to:
QTDIR=/usr/share/qt3/lib

when i compile it again i still get:
mythtv-setup
mythtv-setup: error while loading shared libraries: libmythtv-0.19.so.0: cannot open shared object file: No such file or directory

some information that is has something todo with qt3 is [here]("http://www.mythtv.org/docs/mythtv-HOWTO-4.html#ss4.3")

cause the requested file exists... 

any ideas?[/QUOTE]
And you have the libqt3-mt libraries installed?

---

### Post by mtron on 2006-02-20
thanks. Stupid me.

yeeha! i got the compile now flawlessly for myth 0.19 (with the plugins) with SASC 0.5 and SC 0.5.3 on my ubuntu 5.10 with a Budget card:

Philips Semiconductors SAA7146 (rev 01), Subsystem: Technotrend Systemtechnik GmbH Technotrend-Budget / Hauppauge WinTV-NOVA-CI DVB card.

Build some .deb packages of it ;) (for usual i386 2.6.12-386 Kernel) PM me if you need them.

---

