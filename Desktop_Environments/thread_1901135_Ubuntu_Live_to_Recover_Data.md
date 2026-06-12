---
title: "Ubuntu Live to Recover Data?"
date: 2011-12-27
forum: Desktop Environments
---

### Post by jason100 on 2011-12-27
Hello!

I have my crashed 80GB IDE hard drive hooked up to my mother board. It is the only drive and is connected with the black plug as the master (although I don't think that is relevant).

I heard that it was possible to get the data from it by using Ubuntu Live. I have booted up with Ubuntu 11.10 but my drive does not show up under computer. Using GParted I see the drive as /dev/sda (74.53GiB). Under partitions it is written unallocated with a red exclamation mark (!) and the file system as unallocated with a grey square in front of it. Its size is shown as 74.53GB with dashes under used and unused. There is nothing under flags. Attempting a data rescue gives "command gpart was not found"

Using Terminal and the command "sudo fdisk -l" I also see the drive but its partition table appears to corrupt with the message "This doesn't look like a partition table Probably you selected the wrong device". It is followed by /dev/sda1 to /dev/sda4 with the first having the file system HPFS/NTFS/exFAT.The second is Solaris the third and fourth is BBT.

I have been trying to run TestDisk to recover the lost partition but to no avail. I think there are dependency issues and I have no idea how to install software as there is no internet connection on the computer.

Is there any way I can install TestDisk or any other similar software that will recover the partition so that I can get to my data?

I am running Ubuntu from a 4GB Flash Drive with 500MB reserved for the OS to store changes.

The motherboard is ASUS P5gc-mx with Pentium 4 3.2 GHz processor. It has 1.5 GB of RAM.

When I try to boot from the HDD it gives "error loading operating system".

Please help!

---

### Post by collisionystm on 2011-12-27
post output of

sudo blkid

---

### Post by jason100 on 2011-12-28
> **collisionystm said:**
> post output of

sudo blkid

Hi.

Thanks for your time.

As requested:

/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="05530e1f-1ae8-3e4e-83ad-782e2a7cf073" TYPE="ext2"
/dev/sdb1: LABEL="PENDRIVE" UUID="E03B-3BB5" TYPE="vfat"

---

