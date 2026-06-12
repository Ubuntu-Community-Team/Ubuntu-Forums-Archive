---
title: "how do i remove/uninstall kernel 686"
date: 2006-01-10
forum: General Help
---

### Post by zahidism on 2006-01-10
i actually use 386 because it's faster on my laptop (i dont know why...pentium M dothan 2.0 ghz) and now i would like to remove the 686 from my system (not just remove it from the GRUB start up list) i did something on 686 and it messed up my network connection speed whereas when booting into 386 it's still zippy (im on wireless).  so...

a.) how do i remove/uninstall 686 and what are the ramifications ?

b.) if it's really complicated to do the above, how do i just remove it from the GRUB bootloader (how much space does the kernel take up anywway?)?

thanks!  i love ubuntu and it's support.

---

### Post by jasmuz on 2006-01-10
Open Synaptic and remove the kernel-image-386

---

### Post by o_fortuna on 2006-01-10
Option b is really easy (kernels don't take up too much space). Open up the terminal and type
```
sudo gedit /boot/grub/menu.lst
```
Scroll down to where it says something like "## ## End Default Options ##". Below that lists your kernels. Simply delete (or comment, by placing a '#' in front of the line) all the lines about the kernel 686 (make sure you get rid of the whole paragraph for each one, just to be safe). You'll probably get rid of a paragraph that looks like this:
```
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot
```

This will in no way harm your system (I use this method rather than trying to uninstall a kernel), but it makes those kernels unbootable through the menu.

---

