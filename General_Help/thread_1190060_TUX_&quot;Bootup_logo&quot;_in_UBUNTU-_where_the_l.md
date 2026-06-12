---
title: "TUX &quot;Bootup logo&quot; in UBUNTU- where the losses? Why does not appear?"
date: 2009-06-17
forum: General Help
---

### Post by stoner_di on 2009-06-17
I want to ask someone tried to incorporate the bootup logo ( mini tux in the top left of the display to load the system).
Perform all necessary for this:
- when compiling the kernel, I select this:

Support for frame buffer devices FB->VESA VGA graphics support FB_VESA

Select all in the:

Console display driver support ->

selct all in the:

Bootup logo LOGO->

-in the GRUB, in the file menu.lst fix this row:

kernel /boot/vmlinuz-2.6.29.3 root=UUID=d5b52903-5…. video=vesafb vga=0×0323 ro quiet

-in the file /etc/modprobe.d/blacklist-framebuffer.conf, comment this row:

#blacklist vesafb

-in the file /etc/initramfs-tools/modules, add:

fbcon
vesafb

-in the end update initramfs this command:

update-initramfs -u

In all my UBUNTU not load boot logo!!!!!!!!

I think that the init files have a ban on the emergence of TUX logo. Sorry, can not handle alone. So look for help. I do not want splashy and usplash, because they unnecessarily slow loading Ubuntu to 2-3 seconds.Thus, the system will show a good TUX logo and OS will load quickly. This shows the power of LINUX, that you can always choose what you like it.

I think solving this problem, it will show how flexible is the UBUNTU OS.
This will show how strong is UBUNTU Community.
Thanks in advance.

---

