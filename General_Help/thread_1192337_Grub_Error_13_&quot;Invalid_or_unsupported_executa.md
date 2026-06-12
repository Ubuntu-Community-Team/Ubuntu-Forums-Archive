---
title: "Grub Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2009-06-20
forum: General Help
---

### Post by carfield on 2009-06-20
I've checked google for it, all related to dual boot system having both Windows and Linux. However I only have Linux installed with 2 Kernal, one is 2.6.28-11 and one is 2.6.28-13 , anybody know the reason that I cannot boot with 2.6.28-13 for the message 

Grub Error 13: "Invalid or unsupported executable format"

---

### Post by coffeecat on 2009-06-20
The full error message is (from the grub manual):

> 13 : Invalid or unsupported executable format

This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).Which suggests that grub is having difficulty reading or recognising the kernel. Grub error messages tend to be terse and/or misleading so there's not necessarily anything wrong with your kernel image, so we need to do some detective work. My detective work tells me that you are running Ubuntu Jaunty (from your kernel versions), but I haven't been able to get any further. :wink: So... 

What did you do just before the error appeared? Upgrade? Application installation? Anything else that might give us a clue?

Also, please post the following:
 
The contents of /boot/grub/menu.lst

And the terminal output of these three commands:

> sudo fdisk -l
sudo blkid
ls -lh /boot

**Edit:** just noticed that you said, "I cannot boot with 2.6.28-13". Can you boot OK with the -11 kernel? I'm posting from Jaunty with the -13 kernel so that works OK at least on my system. Perhaps you could clarify and then we could take it from there.

---

### Post by carfield on 2009-06-20
Actually it solved after I run "grub install"....  Not sure about the root cause

---

### Post by bloop on 2009-06-24
I ran into the same problem...I was about to install the latest update, but it told me the boot doesn't have enough space, so i went in, duplicated and removed the files that seem to me to be older kernels (being an adventurous n00bie...). when i restart, i got the error 13 message from the 2.6.27-11. i followed those commands you had posted, and i was wondering if you can help me 

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		86861e37-e8ff-4bb9-b431-3cf5f2e837b0
kernel		/vmlinuz-2.6.27-11-generic root=UUID=76ce889a-347d-435f-b2b9-ada3a0751747 ro quiet splash 
initrd		/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		86861e37-e8ff-4bb9-b431-3cf5f2e837b0
kernel		/vmlinuz-2.6.27-11-generic root=UUID=76ce889a-347d-435f-b2b9-ada3a0751747 ro  single
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10 kernel 2.6.27-11-generic (try this)
uuid		86861e37-e8ff-4bb9-b431-3cf5f2e837b0
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/sdb2 quiet splash
initrd		/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		86861e37-e8ff-4bb9-b431-3cf5f2e837b0
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb5
title		Microsoft Windows XP Professional
root		(hd1,4)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


> ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47751357

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cc97cc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        5718    45921802+   f  W95 Ext'd (LBA)
/dev/sdb2   *        5846        9034    25615642+  83  Linux
/dev/sdb3            5724        5845      979965   82  Linux swap / Solaris
/dev/sdb4            5719        5723       40162+  83  Linux
/dev/sdb5               2        5718    45921771    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f500f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32253   259072191    7  HPFS/NTFS
/dev/sdc2           32254       91201   473499810    7  HPFS/NTFS

> ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="6A64B54F64B51F2F" LABEL="Suga Mama" TYPE="ntfs" 
/dev/sdb2: UUID="76ce889a-347d-435f-b2b9-ada3a0751747" TYPE="ext3" 
/dev/sdb3: UUID="37c3a672-d010-4bf7-a83e-c969cb603e2d" TYPE="swap" 
/dev/sdb4: UUID="86861e37-e8ff-4bb9-b431-3cf5f2e837b0" TYPE="ext3" 
/dev/sdb5: UUID="2E1C8D721C8D363D" LABEL="Lain" TYPE="ntfs" 
/dev/sdc1: UUID="E6783E62783E31A3" LABEL="Video" TYPE="ntfs" 
/dev/sdc2: UUID="2ED84A30D849F71D" LABEL="Music" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 


> ubuntu@ubuntu:~$ ls -lh /boot
total 1.7M
-rw-r--r-- 1 root root  496K 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   90K 2008-10-24 08:29 config-2.6.27-7-generic
-rw-r--r-- 1 root root  122K 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1006K 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root  1.1K 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic

---

### Post by carfield on 2009-06-24
may be you can try running "grub install" also?

---

### Post by rtrevor on 2009-06-24
I've also been getting this error for the new Jaunty kernel (2.6.28-13), but the older one (2.6.28-11) boots fine.

I've recently converted my ext3 partition (which includes /boot) to ext4, and tried installing grub2 (chainloaded). Grub2 also doesn't load (same error message) so I think it may be the conversion to ext4 which needs a grub-install to fix.

Have you also converted to ext4 / tried grub2? Would be useful to pinpoint what is causing this to happen...

---

### Post by Pausanias on 2009-06-29
I'm getting the same error, and same situation as you---converted ext3 to ext4.

This was a serious mistake. I've experienced many problems since converting ext3 to ext4. I should have never done it! This teaches me, and teaches me good.

---

### Post by carfield on 2009-06-29
Well , i think ext4 really fast a lot, althougt the upgrade is not that smooth , still worth the price

---

### Post by Pausanias on 2009-06-30
sudo grub-install fixed it for me, by the way. Thank you.

---

