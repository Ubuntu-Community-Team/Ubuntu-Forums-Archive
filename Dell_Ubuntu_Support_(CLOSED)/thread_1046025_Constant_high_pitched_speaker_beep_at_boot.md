---
title: "Constant high pitched speaker beep at boot"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by eco6905 on 2009-01-21
Hi all,
It's my first post on this forum so hello to all of you.  I found no posts similar to my problem so here it is.

Kubuntu 8.10
Dell Inspiron 1525

The laptop was working fine for the past week or so but last night, when I booted it, it started a very high pitch beep from the PC speaker that forced me to hit the power button immediately.

- This is at boot time and not a BIOS problem.
- I tried booting in single user mode.  Same problem.

I then decided to boot of a liveCD.  The problem was gone.  So I edited **/etc/modprobe.d/blacklist** and added **blacklist pcspkr**.  I shutdown and booted again into the system.

- Same beeping problem.

Can someone help me with this?  The simple solution is a re-installation as the problem clearly comes from the OS and not the system... but that's not really getting rid of the problem.

Any help or pointers are welcome!

---

### Post by Sene on 2009-01-22
I had the same issue with Jaunty before but then removing the module helped.

I booted today and the same scream welcomed me.

I again removed the module ran all the updates and booted up.

The beep was still there when restarting and again when rebooting and this time even when the os was fully loaded and logged in.

Removing the pcspkr module with modprobe or rmmod did not do anything so I just had to boot back in to Windows as that beep drives me insane very quickly.

So until there is a quick solution for this Jaunty is unusable for me.

edit: check also the bug reports at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273397) , [https://bugs.launchpad.net/ubuntu/+bug/284434](https://bugs.launchpad.net/ubuntu/+bug/284434) , [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187/](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187/)

---

### Post by eco6905 on 2009-01-22
Hi Sene,

Thanks for your reply.  It's good to know I am not alone.

The problem is slightly different as the speaker blares at full volume and at a really high pitch.

I have had to reinstall as it was a brand new installation anyway.  If it does happen again, I'll give more info.

---

### Post by Sene on 2009-01-23
Hi,

Found in the bug reports an easy fix.

This is to remove the splash option in your grub menu.lst.

To do this in the bootloader press first e to edit the option selected so you do not have to first hear the beeping.

After you have loaded the OS you can edit the menu.lst itself so next restart can be normal.

---

