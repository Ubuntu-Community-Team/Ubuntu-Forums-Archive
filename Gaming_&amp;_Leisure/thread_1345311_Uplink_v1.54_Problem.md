---
title: "Uplink v1.54 Problem"
date: 2009-12-03
forum: Gaming &amp; Leisure
---

### Post by martydelaney3 on 2009-12-03
When I try to install it comes up with
Verifying archive integrity... All good.
Uncompressing Uplink complete 1.54DOWNLOAD..........................................
/home/marty/.setup4376: error while loading shared libraries: libgtk-1.2.so.0:
cannot open shared object file: No such file or directory
Press Return to close this window...

I'm running xubuntu karmic
Any help would be greatly appreciated.

Edit: I've tried $ sudo apt-get install libgtk1.2 
and all i get are errors

---

### Post by Perfect Storm on 2009-12-04
libgtk1.2 is obsolete and is not maintained anymore, therefore it do not exist in newer releases of Ubuntu.

That said, you can still install libgtk1.2 but it may be more tricky.


**32-bit version of libgtk1.2 in 32-bit Ubuntu**
[http://packages.ubuntu.com/jaunty/i386/libgtk1.2/download](http://packages.ubuntu.com/jaunty/i386/libgtk1.2/download)

Download and click it to install it.


**64-bit version of libgtk1.2 in 64-bit Ubuntu**
[http://packages.ubuntu.com/jaunty/amd64/libgtk1.2/download](http://packages.ubuntu.com/jaunty/amd64/libgtk1.2/download)

Download and click it to install it.


**32-bit version libgtk1.2 in 64-bit Ubuntu**

```
~/Desktop
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
wget http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gtk+1.2/libgtk1.2_1.2.10-18.1build2_i386.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs -i libgtk1.2_1.2.10-18.1build2_i386.deb
```

---

