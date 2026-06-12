---
title: "pic kit 1 on ubuntu"
date: 2007-10-04
forum: Education &amp; Science
---

### Post by hrsvan on 2007-10-04
Hi guys,
I have found this guide on getting the pickit to work;
[http://www.teammojo.org/PICkit/pickit1.html](http://www.teammojo.org/PICkit/pickit1.html)
Following the README on this page I get some problems;
[http://charm.cs.uiuc.edu/users/olawlor/projects/2003/microchip/README.txt](http://charm.cs.uiuc.edu/users/olawlor/projects/2003/microchip/README.txt)

me\computer: cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libusb login

Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/libusb

CVS password:

cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host

I've tried this for some time - in case the server is not online, but it doesn't seem to help. Any ideas?

---

### Post by navaburo on 2007-10-14
try just doing

```
sudo apt-get install libusb-dev
```

also, check out the following, it worked for me!:
[http://ubuntuforums.org/showthread.php?t=123481](http://ubuntuforums.org/showthread.php?t=123481)

---

