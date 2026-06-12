---
title: "[Dell XPS M1530] Unable to boot windows after installing GRUB from ubuntu"
date: 2010-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sakkisays on 2010-01-26
Hi All,

I have a dell XPS M1530 with default installed windows vista home premium.

I installed ubuntu 9.10 on the machine which gave me a GRUB which even lists out the windows and hence it acts as a multi-boot loader.

Recently, i re-installed my windows and the new installation has overridden the GRUB keeping ubuntu active. I wanted to get back to ubuntu so i reinstalled the GRUB from the live CD.

Now the problem is that the GRUB is back and lists both the OS. I am able to get into ubuntu and NOT into Windows.

Please help.

---

### Post by Elfy on 2010-01-26
Hi - can you open a terminal and run the following, paste the outputs here please.

```
ls -al /dev/disk/by-uuid/
sudo fdisk -l
cat /boot/grub/grub.cfg
```

---

### Post by sakkisays on 2010-01-26
Hi,

Thanks for responding.

Here are the outputs:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        1318    10485760    7  HPFS/NTFS
/dev/sda3   *        1318       36997   286595362+   7  HPFS/NTFS
/dev/sda4           36998       38913    15390270    5  Extended
/dev/sda5           36998       38827    14699443+  83  Linux
/dev/sda6           38828       38913      690763+  82  Linux swap / Solaris

SDA3 is the windows partition

Thanks in advance.

---

### Post by sakkisays on 2010-01-29
Hey Guys,

I found the solution. Re-installing GRUB 2 from Ubuntu (using terminal) has done the deal.

It refreshed all the entries in the menu.lst and the entry references are updated. I was able to get into Windows.

Thanks!

---

