---
title: "Kernel Panic - VFS: Unable to mount root fs on unknown-block (0,0) - Part Deux"
date: 2009-02-21
forum: General Help
---

### Post by Epilonsama on 2009-02-21
This bug is simmilar to the one on this thread [http://ubuntuforums.org/showthread.php?t=1040859](http://ubuntuforums.org/showthread.php?t=1040859)
I'm using linux mint, also this is a clean install, I'm cant acces linux, so I cant use any command from linux.
I'm on my windows partition, but I have access to my linux partition.
Heres my grub menu.lst
> 
title Linux Mint 6, kernel 2.6.27-7-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
quiet

title Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single
initrd /boot/initrd.img-2.6.27-7-generic

title Linux Mint 6, kernel Last successful boot
root (hd0,4)
kernel /boot/last-good-boot/vmlinuz root=/dev/sda5 ro quiet splash last-good-boot
quiet

title Linux Mint 6, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
Also i haven't install any kernel that I remember, also I have a peculiar bug where the boot folder repeats itself lot of times or something, don't know if this is related.
Heres the bug(keep in mind its using windows address format):
X:\boot\boot\boot\boot\boot\boot\boot\boot\boot\bo ot\boot\boot\boot\boot\boot\boot\boot\boot\boot\bo ot\boot\boot\boot\boot\boot\boot\boot\boot\boot\bo ot\boot\boot\boot\boot\boot\boot\boot\boot\boot\bo ot\boot\boot\boot\boot\boot\boot\boot\boot\boot

at this final boot it Vista says unspecified
__________________
Contrary to popular belief, America is not a democracy, it is a Chucktatorship.

---

### Post by Epilonsama on 2009-02-21
Is the this a bug in my kernel images?

---

