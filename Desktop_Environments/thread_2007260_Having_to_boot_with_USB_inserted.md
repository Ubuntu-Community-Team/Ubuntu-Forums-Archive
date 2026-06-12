---
title: "Having to boot with USB inserted"
date: 2012-06-20
forum: Desktop Environments
---

### Post by bencouve on 2012-06-20
Hi, I have just installed Ubuntu 64bit on my lap top and so far so good. However, I have one question. If I re-boot and remove the USB that I used for the install then my laptop hangs. If I leave the USB key in then it boots into the OS ok. 

How can I correct this. I did set up the 64bit install with persistence. Could this be the reason?

---

### Post by oldfred on 2012-06-20
Persistence is where you create a USB flash drive installer version with some storage, not  a full install to a hard drive. If flash drive is large enough you can also do a full install to a flash drive.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Are you sure you installed to hard drive? If so you may just have installed the grub2 boot loader to the MBR of the flash drive, not the hard drive. Grub2 normally defaults to installing to sda which normally is the internal drive, but some BIOS promote the flash drive to sda.

Post this.

sudo fdisk -lu

If you just need to repair where grub is at and have the full install in sda:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or When booted into Ubuntu:

sudo grub-install /dev/sda

But grub also remembers where to reinstall on major grub2 updates.

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by bencouve on 2012-06-20
Thanks for your response. I am assuming with the quote bellow you want to see the output so ...

> **oldfred said:**
> 

Post this.

sudo fdisk -lu

...


:~# sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdcf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   616951807   308474880   83  Linux
/dev/sda2       616953854   625141759     4093953    5  Extended
/dev/sda5       616953856   625141759     4093952   82  Linux swap / Solaris

Disk /dev/sdb: 4011 MB, 4011491328 bytes
77 heads, 13 sectors/track, 7827 cylinders, total 7834944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7834943     3913440    b  W95 FAT32


Here it is. Before I do anything here will wait for your response. Thanks again for your help.

---

### Post by oldfred on 2012-06-20
It does look like a full install in sda1. So run this from your install (not liveCD),  and then see if it boots ok.

sudo grub-install /dev/sda

If ok, you then need to update grub's memory to reinstall to sda on updates.

---

### Post by bencouve on 2012-06-20
Ye, that has worked great. Your help is much appreciated, thanks.

---

