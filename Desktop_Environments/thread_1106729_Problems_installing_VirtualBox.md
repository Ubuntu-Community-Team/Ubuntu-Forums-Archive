---
title: "Problems installing VirtualBox"
date: 2009-03-26
forum: Desktop Environments
---

### Post by PicoDeRyo on 2009-03-26
I am a serious Noob when it comes to Linux and I am trying to get VirtualBox up and running, I installed the one from the repositories through add/remove applications, but I kept having problems with the mouse capture. So I tried installing it from Sun's website by using the package installer, but I get this error when I try to install.

dpkg: error processing /tmp/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb (--install):
trying to overwrite '/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko',which is also in package virtualbox-ose-modules-2.6.24-23-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I think something went wrong having the one installed and then installing the newer version. But I have since uninstalled the version from the repositories, and the newer version still doesn't get installed. Any help would be greatly appreciated.

Ryan
running Hardy

---

### Post by namaku0 on 2009-03-26
Remove the module file from old VBox (from repo) manually,
**/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko**,
and then try reinstalling VBox (from Sun) again.

---

### Post by PicoDeRyo on 2009-03-26
how do I remove it manually, like I said I am a complete noob

---

### Post by PicoDeRyo on 2009-03-26
when I get to the misc folder there aren't any files in there. Even after marking 'view hidden files' there is nothing in there. Should I delete the misc folder?

---

### Post by inobe on 2009-03-26
have you rebooted since ?

---

### Post by PicoDeRyo on 2009-03-26
yes I have still same problem

---

### Post by inobe on 2009-03-26
browse again' this time in terminal

```
gksu nautilus
```

if its still empty, go to synaptic' click edit, click fix broken packages.

---

### Post by PicoDeRyo on 2009-03-26
I still couldn't see anything in the misc folder, I tried fixing broken packages and it said 'sucessfully fixed dependency problems' but it happened in no time, like there was nothing to fix

---

### Post by inobe on 2009-03-26
strange

you probably may get more answers in our virtualization forum..

technically you posted in the wrong forum

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by PicoDeRyo on 2009-03-26
Thank you, sorry for posting in the wrong forum, I will post the question in the virtualization forum, thanks again for trying to help

---

