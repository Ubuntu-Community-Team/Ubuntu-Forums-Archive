---
title: "XFCE settings unavailable"
date: 2006-06-01
forum: Desktop Environments
---

### Post by lunatic77 on 2006-06-01
I'm trying to get Xubuntu to work.  After installing kubuntu and some other DE's I decided to play with Xubuntu as well.  So I installed most of the xubuntu-related packages.  Once in XFCE, I can run applications normally.  However, when I try to access the settings menu (either via the Applications menu on the panel, or right-clicking on the desktop), nothing happens (except for a very subtle blinking of my desktop icons).

So...I looked in some of the XFCE documentation, and it seemed that there should be a process running called xfce-mcs-manager.  This process isn't running.  So I tried to run it, and got these errors:

> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I'm wondering if there is some incompatibility between my X configuration and XFCE?

Any help would be very much appreciated.  Thanks!!

**Update:** I realized the above error is simply caused by trying to start an X application from the terminal.  So, I have uninstalled and reinstalled xubuntu, and I have the exact same symptoms (everything's great except that I can't change any settings). ](*,)

---

### Post by lunatic77 on 2006-06-04
Well, I got impatient.  So I decided to blow away my OS and completely reinstall, this time from the Xubuntu Live CD.  Unfortunately, I may never know what I had done wrong; OTOH everything is running fine now.

---

