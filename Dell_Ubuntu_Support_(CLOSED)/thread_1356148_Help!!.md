---
title: "Help!!"
date: 2009-12-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kehlan on 2009-12-15
Hello all, I registered to this website because I am in dire trouble.  I just started with Ubuntu, I don't know my way around the terminal yet.  My wife was using my laptop because she broke the charger on hers.  She said the computer froze and she turned it off.  Thats all I got lol.  When I restarted it, after the Dell screen it goes black.  When I press Enter it reads;

mount: mounting /dev/disk/by-uuid/2a9a1b9f-620e-46b9-ab13-5f3a98d3ee3c on /root failed: Invalid argument
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

What do I need to do? Ubuntu is the only operating system on that computer. Um.. I know I have the latest version if that helps.  I just got done updating it before she got on.  Thanks for the help.

---

### Post by gbrainin on 2009-12-15
Somewhere along the line, it's not finding the right partitions to mount.  Based on your description, it sounds like it might be a problem with GRUB.

Questions:  Was the system booting properly after you installed the new version?

Can you successfully boot off the live CD?

---

### Post by lidex on 2009-12-15
Try booting from the LiveCD in recovery mode and re-install grub. Is this Karmic (9.10)?

---

### Post by mysticdragon on 2009-12-15
Which Ubuntu distribution are you using?  I'm not sure I saw it in your letter.  I'm currently using Ubuntu 9.10, so my input may be a bit limited until I can do some research if it is an earlier version.

---

