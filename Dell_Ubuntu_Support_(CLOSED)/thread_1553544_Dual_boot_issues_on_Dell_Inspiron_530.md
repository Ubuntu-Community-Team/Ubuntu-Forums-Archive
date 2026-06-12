---
title: "Dual boot issues on Dell Inspiron 530"
date: 2010-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by diffusiventity on 2010-08-15
Having attempted to set up a dual boot with Windows Vista (installed first) and Ubuntu 10.04, Windows Vista did not appear on the GRUB screen. Instead I get 3 Ubuntu entries (supposedly updated versions, no problems there) two memtest options and then Windows Recovery Environment.

I have two separate hard drives on my computer and have Vista installed on the first and Ubuntu on the second. What confuses me is that my vista install seems to still be there:

 Looking at System>Administration>Disk Utilities, The first 250GB hard drive has 3 partitions: DELL Utility 66MB FAT, Recovery 11GB NTFS and OS 239GB NTFS. I am sure that the OS partition is Vista, and it is the only "bootable" partition (based on partition flags) that I have on either hard drive.

The second hard drive has 3 partitions too. The first is a 244GB ext4 partition (partition type listed as linux), another called "extended" 6.2GB and a 6.2GB SWAP partition, so it all looks like linux is indeed installed on the second hard drive and Vista on the first.

What's more, I can mount the OS as a media drive on Ubuntu and access all of my Vista files, so surely it can't have been accidentally wiped during the partition process??

Any help would be greatly appreciated. Thankyou.

---

