---
title: "2 Ubuntu boot choices"
date: 2009-04-27
forum: General Help
---

### Post by francisg3 on 2009-04-27
Hello,
I recently installed Ubuntu 9.04 using Wubi installer on my 64bit Windows Vista System. I previously had an older version of Ubuntu installed but I uninstalled it before upgrading to 9.04. When I now boot the system, I am presented with 3 O/S options. One is Vista, the two others are the Ubuntu distro's which both do the same thing. My question is whether or not it is possible to delete one of these choices from the boot option? Thanks for your time!

---

### Post by mikewhatever on 2009-04-27
Backup the menu first with **sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup**.
Now open the menu for editing **gksudo gedit /boot/grub/menu.lst** and delete the options you don't want, save and exit.

---

### Post by francisg3 on 2009-04-27
Wow, quick response. I tried that and the terminal did open up giving me a variety of choices. The following is a part of the window which opened up. I deleted one of the Ubuntu entries without any success. Even with an entry deleted there were 2 Ubuntu options and 1 Windows option on startup...
 
## ## End Default Options ##
 
title Ubuntu 9.04, kernel 2.6.28-11-generic
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=C4AE1CEFAE1CDBAC loop=/ubuntu/disks/root.disk ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic
 
title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=C4AE1CEFAE1CDBAC loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.28-11-generic
 
title Ubuntu 9.04, memtest86+
root ()/ubuntu/disks
kernel /boot/memtest86+.bin

---

### Post by oldos2er on 2009-04-27
I prefer having two kernels on my system, just in case.

 Probably the most efficient way to remove an unwanted kernel is by using a package manager, e.g. Synaptic. This way your menu.lst will automatically be updated.

---

### Post by mikewhatever on 2009-04-27
There is no kernel to remove, there is only one. If you don't want the emtest and recovery mode options, comment them out with the # sign.
Example:
#title Ubuntu 9.04, memtest86+
#root ()/ubuntu/disks
#kernel /boot/memtest86+.bin

---

