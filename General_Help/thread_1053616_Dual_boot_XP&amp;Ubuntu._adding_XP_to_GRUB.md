---
title: "Dual boot XP&amp;Ubuntu. adding XP to GRUB"
date: 2009-01-28
forum: General Help
---

### Post by l0fls on 2009-01-28
OK so i have a 21gb partition on my HD that has windows XP pro SP3 installed
the rest is 280 or so GB partition is ubuntu i am trying to get GRUB to offer me the option to boot from either on start as of right now my grub config goes a little something like this

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		f2a401a2-ef15-4cf8-b81a-4d3baaa53e99
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2a401a2-ef15-4cf8-b81a-4d3baaa53e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		f2a401a2-ef15-4cf8-b81a-4d3baaa53e99
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=f2a401a2-ef15-4cf8-b81a-4d3baaa53e99 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f2a401a2-ef15-4cf8-b81a-4d3baaa53e99
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2a401a2-ef15-4cf8-b81a-4d3baaa53e99 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f2a401a2-ef15-4cf8-b81a-4d3baaa53e99
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f2a401a2-ef15-4cf8-b81a-4d3baaa53e99 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f2a401a2-ef15-4cf8-b81a-4d3baaa53e99
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```





what can i do to add XP to this menu i know i have to add something that goes like this.
 how do i figure out the "root" of my windows partition
title		Windows XP
root		(hd0,0)
makeactive
# chainloader	+1

:KS

---

### Post by @B6Mwu8fN9M on 2009-01-28
This is what I have in my /boot/grub/menu.lst and it boots without problems:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
chainloader	+1

```

---

### Post by l0fls on 2009-01-28
Thanks that worked im writing this now from windows XP :D
ty

---

### Post by mgol on 2009-01-28
> **l0fls said:**
> 
 how do i figure out the "root" of my windows partition
(...)
root		(hd0,0)


It should be (hdX,Y) where X is the disk number (if You have just one HDD it will be 0) and Y is the partition number. You have to count which is the Windows partition and put the number there (**remember to count from 0, not 1!**).

---

### Post by l0fls on 2009-02-03
thanks for the tip

---

