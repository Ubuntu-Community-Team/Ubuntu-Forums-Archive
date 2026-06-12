---
title: "Why two Blank CD-R icons on desktop?"
date: 2021-01-21
forum: Desktop Environments
---

### Post by Eanruig on 2021-01-21
Running Lubuntu 18.04 64 bit on Acer Aspire 5515 laptop.

It is nowhere near a show stopper, just annoying. Duplicate desktop icons appear when a blank CD-R disk is inserted, and a single icon (mounted) appears on the pcmanfm "Places" sidebar. Click on "unmount" flag has no effect; "Expel" flag expels the CD, and both desktop icons vanish.

---

### Post by guiverc on 2021-01-21
That is a known issue with LXDE.  Refer [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1816198](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/1816198)

LXDE is a project on *life-support*; so not a lot gets done.  LXDE uses the GTK2 toolkit (which is depreciated & unmaintained except for small portions used by `gimp` which are supported until `gimp` completes its port to GTK3). 

The LXDE devs did start porting it (*years ago*) to GTK3, there are blogs about it, but it was heavier and slower, they then tested porting it to Qt5 & it performed much better, so they joined with Razor-Qt devs creating the (then) new LXQt project.

Modern Lubuntu uses LXQt now (has since 18.10; 18.04 was the last using LXDE).

The result is, I doubt the issue will be fixed.

---

### Post by Eanruig on 2021-01-26
[EXPLAINED] Thanks for the answer.

---

