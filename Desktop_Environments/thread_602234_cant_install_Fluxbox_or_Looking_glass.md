---
title: "cant install Fluxbox or Looking glass"
date: 2007-11-04
forum: Desktop Environments
---

### Post by kaos13 on 2007-11-04
everytime I try to install I get the following: 

Reading package lists... Done
Building dependency tree
Reading state information... Done
lg3d-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

How could I fix this?
I'm using Ubuntu 7.10

---

### Post by kaos13 on 2007-11-04
any one?

---

### Post by Mazza558 on 2007-11-04
I've got exactly the same problem in terms of looking glass.

---

### Post by Circlingthesun on 2007-11-04
Same here

---

### Post by kaos13 on 2007-11-04
got Fluxbox working using this:  sudo apt-get install fluxbox

Looking Glass still trying

---

### Post by searayman on 2007-11-04
i have the same error for looking glass, i am tryign the lookign glass fofrum:

[http://forums.java.net/jive/thread.jspa?threadID=32812](http://forums.java.net/jive/thread.jspa?threadID=32812)

---

