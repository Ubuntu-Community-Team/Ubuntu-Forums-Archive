---
title: "Mystery Partitions in Dual-Boot Windows + Ubuntu"
date: 2009-05-22
forum: General Help
---

### Post by balloonatic on 2009-05-22
I installed a dual boot of windows 7 and ubuntu a while back and ive been running low on space inmy ubuntu partition so I wanted to see if I could extend my Ubuntu Partition when I discovered that there is a massive 14gb partition within another partition which also contains my Ubuntu.

I've attached a screendump of my gparted.

sda1 is my windows partition
sda3 is the some container (not sure why this exists)
sda7 is (as far as i'm aware) Ubuntu.
sda8&5 are linux-swaps?
sda6 is this very large and mysterious partition.

Can anyone please tell me the purpose of this container and what this sda6 partition, or the swaps are and what purpose they have.

Thanks.

---

### Post by MJBoa on 2009-05-22
/dev/sda3 is the extended partition container, I'm not sure of the correct name but you need it there so you can have more than four partitions. Now I do not know why you have two swaps, you can probably delete the smaller one, I'm not sure why anyone would need 2.

And yeah, /dev/sda7 is your root ubuntu partition.

You can mount the ext2 partition to see what's on it.
You can run these as root to mount it.
mkdir /mnt/ext2
mount -t ext2 /dev/sda6 /mnt/ext2

What probably happened is this, you installed ubuntu or another linux distro and it created a root partition, /dev/sda6, and a linux swap, /dev/sda5. Mount /dev/sda6 to see what's on it but you can probably just delete them.

---

### Post by balloonatic on 2009-05-23
Right, I mounted sda6 and it seemed empty so I figured I should just delete it. I did so, and extended my ubuntu. However, now, my ubuntu won't load from GRUB.

I followed the steps on [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and it loads Windows fine, but gives me "error 22" when I try to load Ubuntu.

Have I ruined my Ubuntu partition by deleting this seemingly void partition?

Anyone know a fix?

Cheers.

[edit] I can access my Ubuntu partition fine from the Live CD.

---

### Post by Legace on 2009-05-23
Post a copy of /boot/grub/menu.lst

---

### Post by balloonatic on 2009-05-23
**This is the grub menu.lst from my Ubuntu partition:**


title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro quiet splash vga=758 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro quiet splash vga=758 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro quiet splash vga=758 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

**I've also attached a screendump of how my gParted looks now**

---

### Post by Legace on 2009-05-23
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root **(hd0,6)**
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro quiet splash vga=758
initrd /boot/initrd.img-2.6.27-9-generic
quiet
```

(hd0,6) translates into sda7, which does not exist.
Your Ubuntu partition is sda5 now, which translates into (hd0,4)

So, change (hd0,6) to (hd0,4) and see how it goes..

By the way, you can delete those old kernels.. So the end result would look like:
```
title Ubuntu 8.10, kernel 2.6.27-9-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro quiet splash vga=758
initrd /boot/initrd.img-2.6.27-9-generic
quiet

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=d8c624dc-da65-4335-ae0e-7b9828f85517 ro single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, memtest86+
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
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by plucky on 2009-05-23
Also check the UUID of the partition as it would have changed ```
sudo blkid
```

Good Luck

---

