---
title: "adding windows 7 to grup"
date: 2010-10-30
forum: Desktop Environments
---

### Post by ggoforth on 2010-10-30
So I'm not exactly sure where to go from here.  This is my setup:

1 TB hard drive that has ubuntu 10.04 installed
1 250 GB hard drive that has windows 7 installed

Ubuntu was installed first, on the TB drive, then I added the 250 gb drive for windows later on.  Both OS's work fine, however, I can only boot into which ever is specified first in the boot disk priority in my bios.  

So, if I want to boot into windows, I have to start the pc, enter the bios, put that drive as top priority, reboot, then I'm in.  Same for Ubuntu.  

Is there a way to get grub to recognize both installs so I can choose at start up which os to load?  I read that if you install windows after ubuntu, windows will wipe the mbr and write a new one, which would leave your linux os hosed until you repair it.  This didn't happen in my case, both os's seem to live independently, for better or worse :)

Thanks for any advice.

gg

---

### Post by ggoforth on 2010-10-30
This is my output from sudo fdisk -ul:


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000deb62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   488394751   244093952    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c46ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1433608469   716803211   83  Linux
/dev/sdb2      1917683710  1953523711    17920001    5  Extended
/dev/sdb5      1917683712  1953523711    17920000   82  Linux swap / Solaris

---

### Post by garvinrick4 on 2010-10-30
Yes just go into Ubuntu install and open a terminal and run:
```
sudo update-grub
```
This will probe for other Operating Systems and drives and add them in Ubuntu's grub2
menu list for you to boot from.
 If you have Ubuntu's drive boot first you will have grub2 to select all to boot. If you have Windows drive boot first you can not use the Grub2 because it has no where on its drive to look for it. (No linux on sda) So just make sdb first in boot order in BiOS. Enjoy your Ubuntu.

---

### Post by ggoforth on 2010-10-31
Exactly what I was looking for!  Works perfect.  Thanks so much!

---

### Post by garvinrick4 on 2010-10-31
You are welcome, enjoy your Ubuntu.

---

