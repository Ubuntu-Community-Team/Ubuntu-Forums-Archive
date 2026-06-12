---
title: "GRUB Boot Loader Problems"
date: 2009-04-10
forum: General Help
---

### Post by Theo103 on 2009-04-10
Hello, I have been using Ubuntu 8.10 for a few months now.
I also have Windows XP Home on my computer.

I installed Windows XP on my second hard drive, then I installed Ubuntu on my first hard drive.
GRUB was loading both of them perfectly.

Then I found an old Maxtor 13GB hard drive in the house, I installed it in my PC and decided to run a second Linux OS.

Since my GF seemed interested in using Ubuntu, I thought she would prefer Kubuntu. So I thought I'd get used to the KDE Interface in case she ever needed any help.

But now GRUB won't work...
When the menu comes up, I have all three Operating Systems showing...
But when I try to Load Kubuntu or Windows, it gives me two separate errors.
When I load Kubuntu
"Error 17: Cannot mount selected partition"

When I load Windows XP
"Error 13: Invalid or unsupported executable format"

It works when I load Ubuntu.

I can change the boot device priority in the BIOS.
In which case, every OS work perfectly fine.

Can anyone help me?

---

### Post by linlux on 2009-04-10
I had the same problem after installing Windows 7

restoring GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It says you need a live CD, but you should also be able to do it from your first ubuntu partition.

---

### Post by Theo103 on 2009-04-10
That doesn't help... =(

Here are the results to fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda09f69c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         498     4000153+   5  Extended
/dev/sda2   *         499        5222    37945530   83  Linux
/dev/sda3            5223       60801   446438317+   7  HPFS/NTFS
/dev/sda5               1         498     4000122   82  Linux swap / Solaris

Disk /dev/sdb: 13.6 GB, 13613064192 bytes
255 heads, 63 sectors/track, 1655 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d092d08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1579    12683286   83  Linux
/dev/sdb2            1580        1655      610470    5  Extended
/dev/sdb5            1580        1655      610438+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f8b1f8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sdc2            6528       19457   103860225    7  HPFS/NTFS

```

On sda2 I have Ubuntu
On sdb1 I have Kubuntu
On sbc1 I have Windows XP

Here is my menu.lst

```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		31ed1769-a012-4575-90bd-c35237b5a743
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31ed1769-a012-4575-90bd-c35237b5a743 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		31ed1769-a012-4575-90bd-c35237b5a743
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=31ed1769-a012-4575-90bd-c35237b5a743 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		31ed1769-a012-4575-90bd-c35237b5a743
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Kubuntu 8.10, kernel 2.6.27-7-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2939cbc9-41f9-4c9e-b4e4-3386948960eb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot

title		Kubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2939cbc9-41f9-4c9e-b4e4-3386948960eb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
rootnoverify 	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

I get an Error 13 when I try to load Windows XP from the GRUB menu "Invalid or unsupported executable format"
I get an Error 17 when I try to load Kubuntu from the GRUB menu "Cannot mount selected partition"

---

### Post by thunderwing on 2009-04-10
hmm, try changing the following from your XP section

from
```

chainloader	+1

```

to
```

chainloader (hd2,0)+1

```

---

### Post by Theo103 on 2009-04-11
Thank you for your help Thunderwing, but it didn't change anything.
I still have an Error 13. ><

What do the map and chainloader section do anyway?
I can sort of see what the map section does, it switches the Windows disk to the first disk, right? Since Windows refuses to comply unless it thinks it's first... kinda sad really ><

---

