---
title: "Create New Partition"
date: 2011-08-02
forum: Desktop Environments
---

### Post by igsen on 2011-08-02
I have a 160gb hard disk drive with ubuntu 10.04 installed. I'm thinking of installing slackware by creating another partition on my drive.
I have downloaded gparted and burned in cd. How do I proceed?

---

### Post by oldfred on 2011-08-02
How many partitions do you have, and do you have an extended partition as that makes it easy to add partitions. If you have used all 4 primary partitions then it becomes more difficult. If you have qestions on what you have post this:
```

sudo fdisk -lu
```

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You also have to decide whos boot loader will be in charge. You can only have one in the MBR. I am not familiar with Slackware but most installs let you choose where to install the grub boot loader. And most be sides Ubuntu let you not install one. If grub legacy I would install grub legacy's boot loader to the same partition as your install and then you have another option in chainloading to it if Ubuntu's grub2's os-prober does not find it.

---

### Post by igsen on 2011-08-03
This is my

sudo fdisk -lu

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ce4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   300574719   150286336   83  Linux
/dev/sda2       300576766   312580095     6001665    5  Extended
/dev/sda5       300576768   312580095     6001664   82  Linux swap / Solaris
```

---

### Post by oldfred on 2011-08-03
You can create two more primary partitions which some systems require and you can expand your extended partition that only has swap in it now into the free space you create by shrinking your Linux partition.I would just shrink sda1 by as much space as you want for slackware and expand extended partition left and put new sda6 into that space.  I have several 20-25GB partitions I use for installing a system to try out.

---

### Post by igsen on 2011-08-04
Thanks oldfred for all the replies. You know what? I ended up deleting ubuntu. My fdisk -lu now looks like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ce4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    62916607    31457280   83  Linux
[COLOR=Red]Partition 1 does not end on cylinder boundary.[/COLOR]
/dev/sda2   *    62916608   182546250    59814821+   7  HPFS/NTFS
/dev/sda3       182546430   312580095    65016833    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       300576768   312580095     6001664   82  Linux swap / Solaris
/dev/sda6       182546432   295665663    56559616   83  Linux
/dev/sda7       295667712   300576767     2454528   82  Linux swap / Solaris
```I've reinstalled ubuntu after xp and thinking of doing the slackware install on /dev/sda1. 
There seem to be an error (red) somewhere. I will investigate further.

---

### Post by igsen on 2011-08-04
I believe the error belongs to another thread. I already marked this thread as solved.

---

### Post by oldfred on 2011-08-04
Ignore that error as it does not apply and should not apply. 

Since hard drives were over 8GB 15 years ago drives have not used cylinders, heads, sectors CHS but have used LBA or large block allocation. Fdisk and some others still check for CHS settings. When Windows Vista and now gparted/Linux changed from sector 63 to start at sector 2048 for better compatibility with large drives SSDs and several other reasons that error has shown up.

---

### Post by igsen on 2011-08-05
> **oldfred said:**
> Ignore that error as it does not apply and should not apply. 

Since hard drives were over 8GB 15 years ago drives have not used cylinders, heads, sectors CHS but have used LBA or large block allocation. Fdisk and some others still check for CHS settings. When Windows Vista and now gparted/Linux changed from sector 63 to start at sector 2048 for better compatibility with large drives SSDs and several other reasons that error has shown up.
Thanks again oldfred for that info.

---

