---
title: "Dualbuntu?"
date: 2009-05-12
forum: Development CD/DVD Image Testing
---

### Post by TheRoach on 2009-05-12
After looking through the forums, and finding nothing, I decided to ask here.
I would like to make a bootable DVD with both versions (32- and 64-bit) installable through a bootmenu. When booting from the DVD, the menu should ask whether to run the 32- of 64-bit version, ideally before giving the screen with the option to run as a Live Ubuntu or installing or... 
Is there a way to do this without changing too much in the system? Would the changed DVD still be redistributable as a *buntu (Multibuntu or something)?

---

### Post by mixmaster on 2009-05-14
I know you can do it with a USB stick - partition the stick and use grub to set up dual boot.  Can you partition a DVD?  If not you would need to do some fancy footwork to ensure that the kernel found the right filesystem.  Maybe boot up into a busybox stub and mount the correct root before bootstrapping the appropriate kernel.

I have a 32/64 multiboot at home off a magazine cover but they cheated - it is a flippy with one on each side.  There's a thought - can you buy 2-sided writable DVD's?

---

### Post by TheRoach on 2009-05-15
I've seen the dual-sided DVD :) I never saw dualsided DVD-Rs or DVD+Rs, though. 

I have almost made it, though there is one obstacle I still need to overcome. With the [Bootable CD Wizard]("http://www.wolfgang-brinkmann.de/bcdw_e.html"), I managed to selectively boot from an isolinux in a subdirectory, but right now I cannot find a way to get the system to mount the squashfs-system in the distro. It tries Ext2, Ext3, ReiserFS and so on, buzt doesn't try squashfs, and when it's done checking those (wrong) systems, the kernel panics.

I am not fully conversant with Linux - it's more of a nodding acquaintance (i.e., I can run it, I can even compile and install a new kernel if needed, but am limited when we come to the details) -, so I was wondering whetherf there is a way to tell the system to specifically check for a squashfs-system?

---

