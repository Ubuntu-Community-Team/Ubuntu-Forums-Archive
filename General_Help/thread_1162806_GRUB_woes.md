---
title: "GRUB woes"
date: 2009-05-18
forum: General Help
---

### Post by Psychosocial on 2009-05-18
Ok so yesterday I installed Ubuntu 9.04 on my system. Today I installed Ubuntu 8.10 again and now I have some problems with the GRUB Bootloader. It does not give me the option to boot into my 9.04 JJ and it only shows 8.10 and my Windows OS as boot options. How can I get back the 9.04 option in GRUB (1.5 version).

---

### Post by labinnsw on 2009-05-18
You should be able to fix this from 8.10
1. Navigate to /boot/grub/menu.lst in your 9.04
2. Copy the relevant lines to /boot/grub/menu.lst on 8.10

To edit the file menu.lst, use:

```
sudo gedit /boot/grub/menu.lst
```

The section you are looking for should look like this:

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

The completed file should look something like this:

> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Ubuntu 9.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0b90258d-5a98-4a62-b3ed-8af9535eaa3f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1

---

