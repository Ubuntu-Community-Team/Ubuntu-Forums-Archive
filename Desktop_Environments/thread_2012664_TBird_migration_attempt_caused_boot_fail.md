---
title: "TBird migration attempt caused boot fail"
date: 2012-06-29
forum: Desktop Environments
---

### Post by jwhiz on 2012-06-29
Hi,

after installing Ubuntu 12.04 on a hard drive with WIndows XP, I had no problems until I attempted to migrate the Thunderbird profile from the Windows partition. After inadvertently cancelling the folder copy operation, all future attempts to copy the folder into Linux reported a lack of space, which seemed odd. When I attempted to restore (copy back) the original TBird Ubuntu profile I received the message that there were 0 bytes left on the drive.

??!!

I decided to restart the system. After trying the various restart options for the Linux system without success, I'm back in XP. Hurray, it still loads...

What might be the problem? With the cut/copy/paste operation causing this apparently fatal problem?

Should I try booting from the Ubuntu CD? 

I can't remember how to wipe a Linux install and start again, but I have the XP cd if I need it too. I've just installed Ubuntu 12.04 last night, mostly very happy, no files yet to lose there and everything backed up from Windows on external media.

---

### Post by jwhiz on 2012-07-06
Well now...I couldn't understand why a cut'n'paste operation would cause any issues, especially such a complete fail.

Perhaps this tells me that it wasn't me (or Tbird): [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187/+index?comments=all)

:shock:

I see a few people mention something odd about the system clock. While using Pangolin happily for a few hours before the Fail, I did get a message a few times about something to do with the system clock (or some other clock function) being set in the future! After changing the desktop clock display, I saw this message again.

So far, the wipe / fixmbr / reinstall seems happy, but I haven't spent more than an hour there. After reading the comments on the above page, I downloaded Mint, which is currently running happily in VMWare Player on the XP side...

---

