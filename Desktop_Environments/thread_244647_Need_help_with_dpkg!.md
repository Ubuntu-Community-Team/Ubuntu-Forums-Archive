---
title: "Need help with dpkg!"
date: 2006-08-26
forum: Desktop Environments
---

### Post by snyper82 on 2006-08-26
I looked everywhere for help on this, I keep recieving this error...

```
:~$ sudo dpkg --configure -a
Setting up gcompris-data (7.2-1ubuntu6) ...
/usr/share/doc-base/gcompris: cannot open control file for reading: No such file or directory
dpkg: error processing gcompris-data (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of madbomber:
 madbomber depends on madbomber-data; however:
  Package madbomber-data is not installed.
dpkg: error processing madbomber (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcompris:
 gcompris depends on gcompris-data (= 7.2-1ubuntu6); however:
  Package gcompris-data is not configured yet.
dpkg: error processing gcompris (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lbreakout2:
 lbreakout2 depends on lbreakout2-data (= 2.5.2-2ubuntu2); however:
  Package lbreakout2-data is not installed.
dpkg: error processing lbreakout2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnome2-common (= 2.14.1-0ubuntu2); however:
  Package libgnome2-common is not installed.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gnome2:
 python2.4-gnome2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing python2.4-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grip:
 grip depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 grip depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 grip depends on libgnomeui-0 (>= 2.8.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing grip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 file-roller depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```

I'm lost at what to do.  I was told to run dpkg --configure -a when I got some errors in snyaptic, and apt-get.

---

