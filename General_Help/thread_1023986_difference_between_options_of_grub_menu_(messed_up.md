---
title: "difference between options of grub menu (messed up both kernels)"
date: 2008-12-28
forum: General Help
---

### Post by lun on 2008-12-28
When i enter the grub menu, there are six options: Ubuntu 8.10 kernel 2.6.27-9, kernel 2.6.27-9 (recovery mode), kernel 2.6.27-7, kernel 2.6.27-7 (recovery mode), the memory test x86 or whatever, and windows xp.  What are the differences between kernel 2.6.27-9 and kernel 2.6.27-7.  Are they actually different kernels?  If not, what are they?

The reason i ask is because i have broken both following this post:

> ```
sudo apt-get install iasl
```


To compile the DSDT just run:

```
iasl DSDT.dsl
```


Once it's compiled put it into the initramfs-tools directory under /etc:

```
sudo cp DSDT.aml /etc/initramfs-tools/
```


You might need to install the initramfs-tools package

```
sudo apt-get install initramfs-toolsand
```


then finally regenerate the initrd image

```
sudo mkinitramfs -o /boot/initrd.img-`uname -r`
```


reboot the machine and then give it a go... 

from this thread (first post on the page):
[http://ubuntuforums.org/showthread.php?t=870681&page=21](http://ubuntuforums.org/showthread.php?t=870681&page=21)

I followed these instructions, which broke the first kernel in grub 2.6.27-9.  So i loaded the second kernel (2.6.27-7) and tried regenerating the initrd.img without the DSDT.aml, but it still hung on boot.  Here is where i really messed up; i tried following the instructions again when i was booted into 2.6.27-7 which wrecked the boot up of that kernel.  I think i realize now that i had to specify which kernel i want to regenerate in /boot when i did this (possibly 'uname -r' tells it to do it to the current kernel booted, but i am unsure what this part of the command does).  But now i cannot boot into ubuntu at all, so my thoughts are trying to do this from using live cd.  I do not want to resort to reformatting with ubuntu, i want to try and fix problems without doing that (which i have relied on too much).

So if anyone can point me in the right direction, that would be great.

Thanks,
nick

---

### Post by 67GTA on 2008-12-29
Try removing the DSDT.aml file from /etc/initramfs-tools and update it. Then try rebooting. The post you followed left out a couple of steps. You have to actually fix the dsdt file before you use it. I can help you with this if you want to try it again.

```
sudo rm /etc/initramfs-tools/DSDT.aml
```
```
sudo update-initramfs -u -k 2.6.27-7-generic
```
```
sudo update-initramfs -u -k 2.6.27-9-generic
```

---

