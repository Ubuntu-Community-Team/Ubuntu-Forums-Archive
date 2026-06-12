---
title: "Dual booting issue when installing XP after ubuntu"
date: 2006-01-06
forum: Desktop Environments
---

### Post by fealz on 2006-01-06
Hey,

my friend(who is not on the forum) is having a problem.  I recently got him to install ubuntu, so we reformatted and repartitioned his one hd completely.  20gigs to linux, 20gigs to windows.  We installed ubuntu first and everything seemed fine, then we installed Windows XP.  Now, grub doesn't give him the option of booting into ubuntu, WinXP just loads by default.  

So, this is what I told him to do:

1) put in the ubuntu disk and press f12 on the dell screen to boot from the disk
2) when the prompt comes up type in "rescue" without quotes and press enter
3) when it asks which partition you want to work on, choose the one ubuntu is installed on(i'm not sure which, but it's probably the first one.. if it says something about ext3, that's the one)
4) remember which partition you pick
5) when you get a prompt, type (without quotes) "grub-install /dev/hdaX" where "X" is the number of the partition.
6) if it says it's locked or you don't have permission or something, type(without quotes) "sudo" before the command.

I thought this would work, but it didn't seem to do anything.. What should he do now?

---

### Post by zahidism on 2006-01-06
im a complete n00b but installing ubuntu first (including grub) and then windows....doesnt that just let windows rewrite the master boot record and therefore it only boots windows?

---

### Post by fealz on 2006-01-06
I think so, yea.. that's why I thought re-installing grub would work... maybe an MBR repair from inside windows?  would that work?

---

