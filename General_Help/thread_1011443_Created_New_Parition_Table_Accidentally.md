---
title: "Created New Parition Table Accidentally"
date: 2008-12-14
forum: General Help
---

### Post by Zerocool3001 on 2008-12-14
Using gparted to try and delete GRUB I accidentally selected "create new partition table". Now I cannot get access to the boot volume. Is there anyway I can get to my data (and I would appreciate it if I could get my system back too, not having to reinstall).

---

### Post by jerome1232 on 2008-12-14
Testdisk should be able to do the job: [http://en.wikipedia.org/wiki/TestDisk]("http://en.wikipedia.org/wiki/TestDisk")

It's in Ubuntu's Repo's.

---

### Post by caljohnsmith on 2008-12-14
As Jerome mentioned, probably testdisk is your best bet. If you would like some help using it, how about opening a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
Then make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partitions.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partitions.

Also, really important, please let me know what you think your partitions should be.

---

### Post by Zerocool3001 on 2008-12-14
I used gpart to try and rebuild the partition table. It seems to have resurrected the main ext3 parition although the swap partitions seem to have been messed up. More importantly, since I assume the MBR was on one of the partitions, when I try to boot from disk GRUB throws error 22. I assume I need to reset the boot device and delete grub but I don't recall how to do that.

Heres the output from fdisk:
```

sudo sfdisk -l

Disk /dev/sda: 20023 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  12555-  12556- 100856036   83  Linux
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

sudo fdisk -lu

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3c733c72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   201712134   100856036   83  Linux

sudo parted /dev/sda print

Model: ATA HDS722516VLAT80 (scsi)
Disk /dev/sda: 165GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  103GB  103GB  primary  ext3         boot 

```

I'm trying to return to the standard Ubuntu installation partition scheme with a single ext3 partition and associated swap partitions (which I believe were 2.4gb)

Thanks for the help.

---

### Post by Zerocool3001 on 2008-12-14
Additionally, while attempting to create new swap partitions myself, gparted errors out while checking the disk and doesn't continue.

---

### Post by Zerocool3001 on 2008-12-14
I think I managed to resurrect my main and swap partitions, but not gparted shows the main partition as the following:

ext3 size 151.01gb used 72.53gb unused 78.48gb

A quick scan with disk usage analyzer shows the following:

size 94.7gb used 16.2gb available 78.5gb

I can't seem to find what is taking up all the space and why the filesystem is not seeing the correct size of the disk.

---

