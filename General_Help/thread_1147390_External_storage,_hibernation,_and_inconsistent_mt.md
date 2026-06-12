---
title: "External storage, hibernation, and inconsistent mtab"
date: 2009-05-03
forum: General Help
---

### Post by spraff on 2009-05-03
Hi everyone.

I have a large USB hard drive with the label Foo, which is mounted as /media/Foo automatically.

Problems arise when I hibernate with the drive plugged-in (and sometimes when I unplug the drive, hibernate, wake, and plug in again) whereby the drive is mounted as /media/Foo-1 or perhaps /media/Foo-2 or even higher. This is more than a minor annoyance since my filesystem is organised by a variety of soft links pointing within /media/Foo which become broken so I have to remount manually.

Sometimes I can't unmount without chasing down processes which own /dev/sdfoo using fuser, but sometimes that's impossble. Right now, for example.

Output of "mount":
/dev/sdb1 on /media/Foo type reiserfs (rw,nosuid,nodev,uhelper=hal)

Output of ls "/dev/sd*"
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdc  /dev/sdc1

I can't forcibly umount /dev/sdb1 (device is busy) and I can't use fuser to query its accessors since it doesn't exist. How do I fix my mtab?

Supplementary: is there any good reason why my drive can't remount to the same label automatically on resume, or why any abrupt disconnect has to cause this problem? Is this an Ubuntu decision, or an upstream one? It seems unnessecarily troublesome to me.

---

