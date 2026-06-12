---
title: "Kernel compiling in Ubuntu is broken"
date: 2009-04-20
forum: General Help
---

### Post by yamokosk on 2009-04-20
I am at my wits end with Ubuntu and kernel compiling. Before you dismiss me with Google/forums searches, know that I have spent the last week and a half trying all means of combinations of vanilla kernels from kernels.org and even "officially" supported kernel sources via apt-get. 

No matter what I try I always received some sort of error. Fortunately for me, the error is different every time.. (sarcasm..). Most of the time, its a random seg fault during the compile process. I must have had these random seg faults occur at least a dozen times. And if I restart the compile process after one of these seg faults, the compile process picks up where it left off with no issues... Wonderful!

My most recent segfault error occured towards the end..

```
  ...
BUILD   arch/x86/boot/bzImage
Root device is (8, 7)
Setup is 12332 bytes (padded to 12800 bytes).
System is 1944 kB
CRC 8c372c78
Kernel: arch/x86/boot/bzImage is ready  (#4)
make[1]: Leaving directory `/usr/src/linux-build-2.6.27-vanilla'
/usr/bin/make  EXTRAVERSION=.10-vanilla  ARCH=i386 \
	                     modules
make[1]: Entering directory `/usr/src/linux-build-2.6.27-vanilla'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  CALL    scripts/checksyscalls.sh
  LD [M]  net/sunrpc/sunrpc.o
  Building modules, stage 2.
  MODPOST 2232 modules
WARNING: modpost: Found 11 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  LD [M]  drivers/net/tokenring/skisa.ko
Segmentation fault
make[2]: *** [drivers/net/tokenring/skisa.ko] Error 139
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-build-2.6.27-vanilla'
make: *** [debian/stamp-build-kernel] Error 2

```

I am a long time Debian/Ubuntu user. But I have NEVER seen something as broken as this.. I have done plenty of kernel compiles with Debian in the past. Besides taking an hour or so, I never ran into ANY problems. And I can't imagine something this fundamental to Linux being this broken.

I have Googled every combination of Ubuntu and kernel compiling I can think of. Besides some nicely written guides, I can't find anyone anywhere with the headaches I have been through. Apart from the custom kernel I am trying to roll, I have a pretty stock Ubuntu installation (8.10).

At this point I am about to give up, wipe 8.10 from my harddrive, start over with (hopefully!) something more stable like Debian or 8.04 and try and get a week of my life back...

---

### Post by calrogman on 2009-04-20
> **yamokosk said:**
> Before you dismiss me with Google/forums searches

Guess what!

I did some searching and found this!

[A whole Youtube playlist on kernel compilation under a Debian environment!]("http://www.youtube.com/watch?v=bH4H9cHPV2s&feature=PlayList&p=D9B5EDCB5CCC7466&index=0&playnext=1")

Google is your friend, not your enemy.

And make sure you```
update-grub
```

---

### Post by sdennie on 2009-04-20
That sounds like a fundamental enough problem that a re-install probably is the most logical step.  If the tools used to build the kernel are segfaulting in random places it almost certainly means that something very fundamental on your machine is corrupted in some subtle way.

---

### Post by yamokosk on 2009-04-20
THATS IT! A youtube video on how to compile a kernel. THANK YOU SO MUCH! Exactly what I needed... Honestly, did you ever pass a reading comprehension test?

@sdennie.. yea that's what I have decided to do. But really, I can't be the only one this has happened to. I don't have any experimental packages just main branch stuff. Oh well.. strike one against Ubuntu.

---

### Post by MartyBuntu on 2009-04-20
I wouldn't rule out RAM errors.

Run MEMTEST just to be sure.

---

### Post by sdennie on 2009-04-20
It could be something very subtle though.  Even a hardware problem.  If you've got bad blocks on your disk and some fundamental thing was sitting on those blocks, you might see this type of behavior.  Or, a bad shutdown or any number of things.  My advice would be to verify the disk is good and re-install.  I don't think the fundamental problem is Ubuntu but some subtle error that has been introduced into some core pieces of software.

Edit:
Yes, bad memory could also cause this.  Or even an over heating machine.

---

