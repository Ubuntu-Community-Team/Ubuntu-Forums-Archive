---
title: "Grub error 13 when booting Windows."
date: 2009-01-28
forum: General Help
---

### Post by utter-imadness on 2009-01-28
Hello. I just installed Windows Vista on partition /sda3 but when I try to boot from grub I get 'Error 13: Invalid or unsupported executable format". I have EasyBCD installed on my Vista partition as well but I have grub as my main bootloader. Here's some info of my configuration:

```
sudo fdisk -l 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09e709e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         829     6658911   83  Linux
/dev/sda2   *         830       22354   172899562+  83  Linux
/dev/sda3           22355       30139    62533012+   7  HPFS/NTFS
/dev/sda4           30140       30401     2104515    5  Extended
/dev/sda5           30140       30401     2104483+  82  Linux swap / Solaris
```

```
title 		Ubuntu 8.10, kernel 2.6.27-11-generic
kernel 		/boot/vmlinuz-2.6.27-11-generic root=UUID=1c2f38b1-00d4-4c45-b1df-973cfd808691 ro noquiet splash
initrd 		/boot/initrd.img-2.6.27-11-generic

title 		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel 		/boot/vmlinuz-2.6.27-11-generic root=UUID=1c2f38b1-00d4-4c45-b1df-973cfd808691 ro  single
initrd 		/boot/initrd.img-2.6.27-11-generic

title 		Ubuntu 8.10, kernel 2.6.27-7-generic
kernel 		/boot/vmlinuz-2.6.27-7-generic root=UUID=1c2f38b1-00d4-4c45-b1df-973cfd808691 ro quiet splash
initrd 		/boot/initrd.img-2.6.27-7-generic

title 		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel 		/boot/vmlinuz-2.6.27-7-generic root=UUID=1c2f38b1-00d4-4c45-b1df-973cfd808691 ro  single
initrd 		/boot/initrd.img-2.6.27-7-generic

title 		Ubuntu 8.10, memtest86+
kernel 		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title 		Windows Vista/Longhorn (loader)
root 		(hd0,1)
chainloader +1
savedefault
makeactive
```

Any help is really appreciated!

---

### Post by birddog165 on 2009-01-28
It looks like there is a problem with the file system:
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

---

### Post by caljohnsmith on 2009-01-28
How about trying instead:
```
title 		Windows Vista/Longhorn (loader)
root 		[COLOR="Blue"](hd0,2)[/COLOR]
chainloader +1
savedefault
makeactive
```
(hd0,2) would be sda3, so I think you might have better luck with that rather than (hd0,1). But if you run into problems, let us know. :)

---

### Post by utter-imadness on 2009-01-28
Oh wow. I spent hours trying to fix this and it was just a digit off. Thank you so much caljohnsmith. You've saved me once again!

---

### Post by caljohnsmith on 2009-01-28
"Grub's World" is quite convoluted to say the least, so I can totally understand making that type of mistake (I've done it too); I'm glad that was the only problem. Cheers and enjoy Vista and Ubuntu. :)

---

