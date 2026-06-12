---
title: "Screen resolution problem"
date: 2005-05-13
forum: Desktop Environments
---

### Post by fredski on 2005-05-13
I have a 14" monitor that will only run at 60mhz at 800 x 600. I used another monitor to set the desktop up to use those settings. but when i plugin my 14" it works until i reboot. then the screens all wavy and flickering, i enter my password on the keyboard and press enter, then the desktop loads and my desktop is displayed ok again. how can I set the system to boot at that resolution and refresh rate and not only when the desktop is fully loaded?

any help would be much appreciated.  This is my first break from windows, so a step by step guide would be nice :)

---

### Post by harryc on 2005-05-13
Add the following to the 'kernel' line in your /boot/grub/menu.lst file.

vga=0x314

---

### Post by fredski on 2005-05-14
Nope that didnt work :(

added it to the end of each kernel line, 

I tried adding it to
 ##default start options#
# vga=0x314

then i tried add in it to
##end default options#
vga=0x314

still the same problem, what am i doing wrong??

---

### Post by danpre on 2005-05-14
[QUOTE=fredski]I have a 14" monitor that will only run at 60mhz at 800 x 600. I used another monitor to set the desktop up to use those settings. but when i plugin my 14" it works until i reboot. then the screens all wavy and flickering, i enter my password on the keyboard and press enter, then the desktop loads and my desktop is displayed ok again. how can I set the system to boot at that resolution and refresh rate and not only when the desktop is fully loaded?

any help would be much appreciated.  This is my first break from windows, so a step by step guide would be nice :)[/QUOTE]

go to /boot/grub/menu.lst

find a line looking like this:
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash

and at the end of the line add vga=0x314

so the line will look like this:

kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash vga=0x318

DANIeL

---

