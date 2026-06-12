---
title: "gnome system monitor applet - hard disk activity"
date: 2009-06-04
forum: Desktop Environments
---

### Post by fermulator on 2009-06-04
This is a continuation of an old post (which was never answered): [http://ubuntuforums.org/showthread.php?t=400271&highlight=gnome+system+monitor+applet+disk+activity](http://ubuntuforums.org/showthread.php?t=400271&highlight=gnome+system+monitor+applet+disk+activity)

I too find that the gnome system monitor applet monitors /dev/hd and /dev/sd drives, but does not monitor mdadm RAID devices, nor does it monitor dmraid (/dev/mapper) devices.

How can we configure the hard disc activity portion of this applet to also monitor such devices?

---

### Post by fermulator on 2009-06-12
I found an old bug report on this issue and reopened: [https://bugs.launchpad.net/bugs/126618](https://bugs.launchpad.net/bugs/126618)

---

### Post by danstoner on 2010-07-30
I believe this issue is a gnome bug, the upstream current bug report for this issue is

[https://bugzilla.gnome.org/show_bug.cgi?id=160441](https://bugzilla.gnome.org/show_bug.cgi?id=160441)

---

