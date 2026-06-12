---
title: "Gstm Help Install"
date: 2006-05-31
forum: Desktop Environments
---

### Post by dizzaniix on 2006-05-31
I'm having a problem with installing Gnome SSH Tunnel Manager.
I'm using the debian package..
Heres the output I recieve.

danv@silver:~/Desktop$ sudo dpkg -i gstm_0.3-1_i386.deb
Selecting previously deselected package gstm.
(Reading database ... 89939 files and directories currently installed.)
Unpacking gstm (from gstm_0.3-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gstm:
 gstm depends on libbonobo2-0 (>= 2.13.0); however:
  Version of libbonobo2-0 on system is 2.10.1-0ubuntu1.
 gstm depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 gstm depends on libglib2.0-0 (>= 2.9.3); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 gstm depends on libgnomeui-0 (>= 2.13.0); however:
  Version of libgnomeui-0 on system is 2.12.0-0ubuntu1.
 gstm depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Version of libgnomevfs2-0 on system is 2.12.1-0ubuntu2.
 gstm depends on libpango1.0-0 (>= 1.11.99); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 gstm depends on libxml2 (>= 2.6.23); however:
  Version of libxml2 on system is 2.6.21-0ubuntu1.
dpkg: error processing gstm (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstm

---

### Post by butlershouse on 2006-10-03
Ive just installed gtsm under Ubuntu 6.06 LTS

It used the Gnome Package installer to allow me to select the .deb package straight from sourceforge ( via kent ) and it installed and worked directly  .

I know its no help to you but since you posted in May I imagine that much has now been fixed !


Nik

I hope we can see gtsm moved to the libraries some time soon

---

