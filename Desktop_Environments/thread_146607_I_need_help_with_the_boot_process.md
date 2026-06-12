---
title: "I need help with the boot process"
date: 2006-03-18
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-18
I have two hard drives - /dev/hda and /dev/hdb.

I have Ubuntu 5.10 installed on /dev/hda so the MBR looks at /boot/grub/menu.lst on /dev/hda to determine which operating system to boot.

Suppose I want to install Fedora Core 5 on /dev/hdb, then, after FC5 installs grub, the MBR will look at the menu.lst on /dev/hdb to determine which operating system to boot.

This works great.. except.. suppose I no longer want an OS on /dev/hdb and want to format /dev/hdb and use it to store MP3's or video but keep Ubuntu on /dev/hda as my main OS. Once I format /dev/hdb, the MBR, which is looking for menu.lst on /dev/hdb, won't be able to determine which OS to boot because the menu.lst file is no longer there after the format. Therefore, my box will no longer boot at all.

How do I fix this problem? Is there a method of "cleaning" out the MBR and telling it where to look for menu/lst?

---

### Post by Ramses de Norre on 2006-03-18
Reinstall grub on the other partition.
I'm not in ubuntu right now, but I think you need to run 'grub' in terminal and then do grub-install hd(x,x) with (x,x) the disk number and partition number starting from 0.
But I'm not totally sure it are the right commands (can't check now).

---

