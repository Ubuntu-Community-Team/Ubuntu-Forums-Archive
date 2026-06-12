---
title: "Installed Ubuntu 7.10 on my Inspiron 1420 and now I can't boot or reinstall Vista"
date: 2008-01-11
forum: Dell  Ubuntu Support
---

### Post by hjhtw on 2008-01-11
I'm absolutely new to Linux and still foolish with computers in general enough to do some foolish and over-hasty things. In this case, I downloaded the Ubuntu 7 live CD, booted linux from the it a few times, liked it, and decided to install.

I simply worked through the installer on the live CD, without previously partitioning my drive. I believe that the installer did perform some partitioning, but I don't know quite what it did.

After installing Ubuntu, I can boot it just fine. However, it is very important to me that I also be able to boot Vista on occasion. Even more importantly, I want to be able to access the files that I had on the disk before I installed Ubuntu. I can't seem to be able to do either.

I tried repairing Vista startup with the Vista DVD that came with my Dell, but it fails. Windows startup repair cannot find my Vista installation. I cannot even seem to reinstall Windows, as Windows can no longer seem to use my hard drive partitions in their current format.

Ultimately, as I said, I want to be able to dual boot Ubuntu and Vista. First, I just need to be able to get back into Vista and access my files as I did before Ubuntu.

Needless to say, any help or advice is immensely appreciated. I will be glad to provide more descriptive information, if I am told what information to provide.

- a foolish greenhorn

---

### Post by Amstell on 2008-01-11
dont' know if this may help you but

[http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

or

edit you grub

 /boot/grub/menu.lst

It has instructions but here is a copy of mine for you.

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0a67907c-0f12-4bf7-b38d-937138d5c700 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0a67907c-0f12-4bf7-b38d-937138d5c700 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by natehall on 2008-01-11
Post the results of this command :
sudo fdisk -l
That will show how your harddrive is partitoned right now.

---

### Post by hjhtw on 2008-01-11
Here is the output of sudo fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris
```

I am also testing the  results of editing /boot/grub/menu.lst

---

### Post by logos34 on 2008-01-11
sorry to break this to you, but it looks like Ubuntu overwrote your entire disk.  

hasta la vista, vista...

If there was critical data on it you need to recover, try TestDisk.

---

