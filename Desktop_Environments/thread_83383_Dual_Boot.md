---
title: "Dual Boot"
date: 2005-10-28
forum: Desktop Environments
---

### Post by sicness on 2005-10-28
Hey all,

Here's what I want to do:

Dual boot Breezy Ubuntu 5.10 with Windows XP using either Lilo or Grub.

My setup:

Right now I've got WinXP on one hdd and Ubuntu on another, and when I want to boot to the other I just switch the cables (my case is open and right infront of me so it's really easy).  However I'd rather try and figure out how to get dual boot working.

What I need:

I need to know if it's possible to dual boot these hdds without re-installing the OS on either of the drives.  Beyond that, if it is possible, a link to a site or just some info would be great.

Thanks in advance.

---

### Post by Kyral on 2005-10-28
I *think* booting the LiveCD while both are plugged in and running "install-grub" should do it.

Just be wary to install it onto the MBR of whatever HD the BIOS is looking for boot first.

---

### Post by sicness on 2005-10-28
So the MBR should be on the HDD that's on master right?

ps. thanks for the quick reply

---

### Post by Kyral on 2005-10-28
Yah.

GRUB should take care of the rest.

---

### Post by sicness on 2005-10-28
Great.  Thanks, wish me luck.

I'll tell you how it goes....unless I can't boot my system up :P

---

