---
title: "CRC Failed during kernel decompress"
date: 2006-06-25
forum: Desktop Environments
---

### Post by sandpaperback on 2006-06-25
I assume this must have happened with one of the auto updates, but suddenly, if I choose Ubuntu from my GRUB loader, I get a CRC Failed message.  If I choose 'e' on the GRUB menu and choose 'boot' it works fine.  But if I just let it go or choose the Ubuntu option directly from GRUB, it fails.

Oddly enough, I tried loading from the LiveCD that I used to install in the first place (and have run several times before and after the install) and got the same CRC Failed message.

Any ideas on how to proceed?

---

### Post by tonyr on 2006-06-25
Post your /boot/grub/menu.lst here.  What is the order of the boot selections
on the displayed GRUB menu?

---

### Post by sandpaperback on 2006-06-26
Oddly enough, it seems to be working now though I didn't change anything.  I let it boot up normally when I got home last night and it worked fine.  For the sake of thoroughness though, here's my menu.lst.  Relevant section anyway.  Default set to 0.


```
title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		______________________________
root

title		*** FOR EMERGENCY USE ONLY ***
root

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin 
boot


```

---

### Post by tonyr on 2006-06-26
Well, I guess ya can't fix it if it ain't broke.

---

