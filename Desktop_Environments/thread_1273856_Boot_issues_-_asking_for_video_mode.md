---
title: "Boot issues - asking for video mode"
date: 2009-09-23
forum: Desktop Environments
---

### Post by timClicks on 2009-09-23
Hi all,

When I boot up via GRUB Legacy, I'm asked to select a video mode. At the moment it seems a script is telling the computer to attempt to run video mode 316 - and then complains this doesn't exist. Every time I reboot, I need to select video mode 315...

Does anyone know where this config script is located?

---

### Post by clonne4crw on 2009-09-27
the GRUB config file is

/boot/grub/menu.1st. Video mode is defined in the kernel line.

---

### Post by Minsky on 2009-09-28
315 is a hex number which you first need to convert to decimal (789) and then append it to the **kernel** line in menu.lst, like this:-

title       Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        632df6fd8-fabb-4a5f-6d1f-81ce0f52cde6
kernel      /boot/vmlinuz-2.6.28-15-generic root=UUID=632df6fd8-fabb-4a5f-6d1f-81ce0f52cde6 ro quiet splash vga=789
initrd      /boot/initrd.img-2.6.28-15-generic
quiet

You need to be logged in as root to be able to edit menu.lst

---

