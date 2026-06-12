---
title: "Problems Loading Grub Bootloader"
date: 2008-06-08
forum: Desktop Environments
---

### Post by tonyh79 on 2008-06-08
Hello All

I'm havina a big problem with my desktop computer. Yesterday, when I was was starting my computer, the Ubuntu loader froze and I had to press the reset button on my box, and once it restarted I had not boot loader.  I tried restarting several times and same thing.  The bios loads, and right after it just takes me to a black screen with a little underscore character on the top left corner.  It's not a prompt since I can't type in anything.  The only keys that do anything are Ctrl+Alt+Del which just reboots my system and does the same thing.  I thing it may be that the boot loader got corrupted or something.  Any help or advise that anyone could give me I would greatly appreciate it.

I have a dual boot system with Ubuntu 8.0.4 LTS and Windows XP, and my system runs on a Asus A8N32-SLI Deluxe motherboard.

Thank you.

---

### Post by tonyh79 on 2008-06-08
I figured it out!

I inserted the Live CD and restored the grub menu file in /boot/grub/menu.lst with a backup.

Thank you anyway!

---

