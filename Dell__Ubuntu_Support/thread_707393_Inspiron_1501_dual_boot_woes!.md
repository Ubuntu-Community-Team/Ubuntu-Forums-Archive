---
title: "Inspiron 1501 dual boot woes!"
date: 2008-02-25
forum: Dell  Ubuntu Support
---

### Post by bradford72 on 2008-02-25
Okay, here we go again!  I recently installed kubuntu 7.10 amd64 on my Dell Inspiron 1501.  So far it looks and runs great, except for one problem, I can not (or have not yet successfully) dual boot with Vista.  I have kubuntu on its own partition, and my windows partition is still intact (I have it mounted, read only, on /media/windows...great success!).  I'm pretty sure I can fix the problem by modifying my grub menu.lst file (or at least I'm willing to try that) but I forget the  path and filename to start windows, and grub seems to wanna know this stuff...any help here?

---

### Post by jeffus_il on 2008-02-25
The easiest way id to download and burn "supergrubdisk" and to boot with it. It should discover your windows partition and fix grub.
[http://www.geocities.com/supergrubdisk/](http://www.geocities.com/supergrubdisk/)

or rather this:
[http://sgd.benjamin-butschko.de/](http://sgd.benjamin-butschko.de/)

---

### Post by bradford72 on 2008-02-25
ooooh! super grub!!??  I'm gonna try it tonight.  Thanks a lot jeffus, and everybody else who likes to 'buntu too! My computer is fun again!

---

### Post by jeffus_il on 2008-02-28
When does the supergrub disk give you a problem? When you boot from it?

---

### Post by provisional_idiot on 2008-02-28
im not sure about vista, but you can add the kernel to the menu.lst  in /boot/grub for other linux dist.

for example i dual boot ubuntu/fedora, here's my /boot/grub/menu.lst:

> ## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=91860dda-6fc5-4915-bf74-e6bcf7422212 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title 		Fedora 8
root 		(hd0,0)
kernel		/duplicate ro root=/dev/VolGroup00/LogVol00
initrd		/duplicateinit

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=91860dda-6fc5-4915-bf74-e6bcf7422212 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/memtest86+.bin
quietge

### END DEBIAN AUTOMAGIC KERNELS LIST 

so maybe you can just add an entry for vista:

title Windows Vista
root (hdX,Y)                                                               // X=which harddrive Y=which partition where the kernel is located
kernel pathofkernel options/boot_parameters // note that the path of the kernel is relative to hdX,Y, which in my case is mounted onto /boot
initrd pathofinitrdfile                                               // you might not need this one if windows boots the kernel all at once

so after appending the menu.lst file with an entry like about, just reboot and press escape to get the grub menu. choose the entry Windows Vista

maybe this works, maybe not

oh yeah...this only works if your boot loader is GRUB (which is probably is)

---

