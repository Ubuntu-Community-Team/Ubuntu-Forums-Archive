---
title: "gnomemeeting makes everything freeze"
date: 2006-02-18
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-18
I have a problem with gnome meeting, I installed the spca5xx driver for my webcam and it worked perfect, untill yesterday I updated my linux headers and kernel image (but I have still got the same kernel, 2.6.12-10-k7).
After reboot gnome meeting makes the whole system crash, nothing responds anymore.
Could it be that I have to recompile the spca5xx driver? If so how do I delete the previous module?
And where can I find logs for the hang up? There are no fault messages in the Xorg.0.log.old file.

---

### Post by chele on 2006-02-18
Yes, you will need to reinstall the driver. Try [EasyCam]("https://wiki.ubuntu.com/Webcam")

---

### Post by Ramses de Norre on 2006-02-18
Easy cam doesn't work for my creative NX pro. But I have allready recompiled the driver and it seems to work again.
Only question, why can't I use checkinstall to make it a .deb?
```
sudo checkinstall -D make install
``` starts the program but he fails when compiling, ```
Building Debian package... FAILED!

*** Failed to build the package

```
But I don't remember the log and I don't know its location.
```
sudo make install
```
worked just like normal.
Any idea what the problem could be? I like using checkinstall more then just compiling from source.

---

### Post by kaamos on 2006-02-18
It's most likely conflicting with another package. When it fails, it asks you if you'd wish to see the log.

---

