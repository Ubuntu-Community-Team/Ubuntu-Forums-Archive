---
title: "Cant install programs"
date: 2005-12-01
forum: Desktop Environments
---

### Post by anirbanb_007 on 2005-12-01
I have shifted to linux from windows very recently. I cant understand how we install third party programs. For example I tried installing yahoo messenger and used the command line given **dpkg -i <filename>**. But the message I get is the following:

[COLOR="Green"](Reading database ... 58022 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/COLOR]

I think that pixbuf2 and all must be some essential component but where do I get them and how do I install them. I couldnt not find them in Synaptic Package Manager.

---

### Post by aysiu on 2005-12-01
Read these:
[http://www.ubuntuforums.org/showthread.php?t=92916](http://www.ubuntuforums.org/showthread.php?t=92916)
[http://www.ubuntuforums.org/showthread.php?t=93906](http://www.ubuntuforums.org/showthread.php?t=93906)
[http://www.ubuntuforums.org/showthread.php?t=87106](http://www.ubuntuforums.org/showthread.php?t=87106)

---

