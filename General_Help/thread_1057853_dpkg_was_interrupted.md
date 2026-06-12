---
title: "dpkg was interrupted"
date: 2009-02-02
forum: General Help
---

### Post by lorna.s. on 2009-02-02
update manger error, ub8.10 intrepid 26.7.11 "dpkg was interrupted, you must manually run ....." removed sources from etc/apt/source.lists, leaving only the intrepid updates, changed servers for updates (twice - us main and virginmedia uk) and tried again.  error as below 


TERMINAL
Hit [http://ubuntu.virginmedia.com](http://ubuntu.virginmedia.com) intrepid-updates/universe Packages
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

:~$ sudo dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Rise, lather and repeat. I really would appreciate help on this one, having read this thread, on reboot ensuring no package manager is running, stopped start up applications also. Obviously I have missed something somewhere?

sources.list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) intrepid-security main restricted

deb [http://ubuntu.virginmedia.com/archive/](http://ubuntu.virginmedia.com/archive/) intrepid-updates restricted main

---

### Post by balaknair on 2009-02-02
Apparently dpkg is choking on some borked package.
Try the following commands in a terminal

*sudo dpkg -l | grep -v ^ii *

This will list any packages not installed correctly.
Then remove the faulty package wuth

*sudo dpkg --purge remove _faulty package_*

(Replace *_faulty package_* with the name of the offending package.)

Hope this helps.
All the best.

---

### Post by lorna.s. on 2009-02-02
oh wow, thanks, started at the bottom worked my way up my apparently horked installed packages... there was a lot! Package manager is getting updates now, very grateful for your help there. lorna

---

### Post by balaknair on 2009-02-02
Glad to help.
Have fun.

---

