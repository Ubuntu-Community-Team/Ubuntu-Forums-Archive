---
title: "How to change virtual terminal screen size"
date: 2005-12-15
forum: General Help
---

### Post by fergus.b on 2005-12-15
When I go to a new virtual terminal (eg: <alt>+<ctl>+F1) the screen size is too high and the prompt disappears off the bottom when the screen fills up. How do I change this? 

I have an Acer laptop (Aspire 1362LC) with some kind of Intel (I think) graphics adapter.

---

### Post by silex on 2005-12-15
This resolution is set at boot by a setting in the menu.lst file that grub reads (assuming you use grub from here on out, its the default bootloader for ubuntu).  Open up menu.lst with your favorite text editor as root:
```
sudo nano /boot/grub/menu.lst
```

Now, scroll down for a while and find the boot entry you want to change the resolution of; usually its the first one that is uncommented.  Now, add vga=### to the end of the "kernel" line you want to use (again, should be part of the section of the kernel you usually boot into), where ### is one of the following numbers:

.................640x480.........800x600.......... 1024x768........1280x1024
8 bpp............769................771............. .....773 ..............775
16 bpp ..........785 ...............788.................791............ ....794
32 bpp...........786 ...............789.................792............ ....795

For myself, I use 1280x1024 at 32bpp, so i added vga=795 to the end of the line.  Then when you reboot and select the boot option that you edited, all your bootup information and any extra virtual terminals you switch to will be at your desired resolution.

For example, here is the entry in my menu.lst that I boot with.  Notice the end of the kernel line:
```
title           Ubuntu, kernel 2.6.12-10-686-smp
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda2 ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.12-10-686-smp
savedefault
boot

```

---

### Post by fergus.b on 2005-12-15
Superb! Thanks very much! A quick, detailed and extremely helpful reply :D

* Tips hat to silex

---

