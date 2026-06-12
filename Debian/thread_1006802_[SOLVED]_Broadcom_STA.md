---
title: "[SOLVED] Broadcom STA"
date: 2008-12-09
forum: Debian
---

### Post by COLiNx86 on 2008-12-09
I recently switched back to Debian Lenny (gnome this time, much faster). But now I can't get the Broadcom driver to install, or even compile for that matter. I type in 
```
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
```
But it gives me errors about there not being a makefile. what can I do to make it compile? And i have the headers installed (or at least I should since I installed them last night)

---

### Post by albinootje on 2008-12-09
Are there install-instructions with it ? 
Is ./configure not needed first ? 
Is there a file called autogen.sh ? 
Did you install build-essential ?

---

### Post by Ayuthia on 2008-12-09
Are you sure that you are in the right directory?  It sounds like you might not be.  If you think you are, can you post the results of:
```
ls -a
```from the directory where you are compiling the wl driver?

---

### Post by COLiNx86 on 2008-12-09
> **Ayuthia said:**
> Are you sure that you are in the right directory?  It sounds like you might not be.  If you think you are, can you post the results of:
```
ls -a
```from the directory where you are compiling the wl driver?
it says
```
.  ..  lib  Makefile  src
```

EDIT: ok I know what the problem is the kernel headers aren't installing right. Now the next problem, how *do* I install them if synaptic and apt-get aren't working?

---

