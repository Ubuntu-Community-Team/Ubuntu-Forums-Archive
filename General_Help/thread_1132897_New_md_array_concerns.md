---
title: "New md array concerns"
date: 2009-04-22
forum: General Help
---

### Post by _2009 on 2009-04-22
Hi,

I've just installed a new 4 disk raid 5 array in our server and I have a couple of concerns that you experts might be able to relieve!

$ sudo mdadm --detail /dev/md0

```
/dev/md0:		
        Version : 00.90		
  Creation Time : Tue Apr 21 22:26:11 2009		
     Raid Level : raid5		
     Array Size : 625142272 (596.18 GiB 640.15 GB)		
  Used Dev Size : 312571136 (298.09 GiB 320.07 GB)		
   Raid Devices : 3		
  Total Devices : 4		
Preferred Minor : 0		
    Persistence : Superblock is persistent		
		
    Update Time : Wed Apr 22 16:20:34 2009		
          State : clean		
 Active Devices : 3		
Working Devices : 4		
 Failed Devices : 0		
  Spare Devices : 1		
		
         Layout : left-symmetric		
     Chunk Size : 64K		
		
           UUID : fbf61ee0:7101193a:74c606ae:4287211e (local to host s-1)		
         Events : 0.194		
		
    Number   Major   Minor   RaidDevice State		
       0       8        0        0      active sync   /dev/sda		
       1       8       48        1      active sync   /dev/sdd		
       2       8       32        2      active sync   /dev/sdc		
		
       3       8       16        -      spare   /dev/sdb
```		


1. On boot the lilo reports a duplicate disk ID. This duplicate is visible from the output of:

$ sudo fdisk -l

```
Disk /dev/sda: 320.0 GB	 320072933376 bytes	
255 heads	 63 sectors/track	 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes		
Disk identifier: 0x00000000		
		
Disk /dev/sda doesn't contain a valid partition table		
		
Disk /dev/sdb: 320.0 GB	 320072933376 bytes	
255 heads	 63 sectors/track	 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes		
Disk identifier: [COLOR="Lime"]0x5d641cae[/COLOR]
		
   Device Boot      Start         End      Blocks   Id  System		
/dev/sdb1               1       38913   312568641   fd  Linux raid autodetect		
		
Disk /dev/sdc: 320.0 GB	 320072933376 bytes	
255 heads	 63 sectors/track	 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes		
Disk identifier: [COLOR="Lime"]0x5d641cae[/COLOR]
		
   Device Boot      Start         End      Blocks   Id  System		
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect		
		
Disk /dev/sdd: 320.0 GB	 320072933376 bytes	
255 heads	 63 sectors/track	 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes		
Disk identifier: [COLOR="Lime"]0x5d641cae[/COLOR]		
		
   Device Boot      Start         End      Blocks   Id  System		
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect
```		

Is this anything to worry about, will it come back to bite me?

The fdisk output also raised another issue: /dev/sda "doesn't contain a valid partition table". Is this normal for a disk in an array?

Feel free to ask any questions that come to mind...

Cheers,
_2009

---

### Post by fjgaude on 2009-04-22
> The fdisk output also raised another issue: /dev/sda "doesn't contain a valid partition table". Is this normal for a disk in an array?

No, it is not normal... something is amiss here.

Having the same identifier for two disks, I've never seen such before. How, pray, did this come about? What have you been doing with the drives before creating the array?

---

### Post by _2009 on 2009-04-23
I thought so, especially as the other 3 disks in the array don't display this message. Also the disk ID on /dev/sda is 0x00000000, which is weird?

> What have you been doing with the drives before creating the array?
Nothing, they're brand new, I just unwrapped the static bag and installed them in the case. Used fdisk to create a new primary partition filling the drive and gave them all the "Linux Raid autodetect" partition code.

What should I do?

Thanks for your help,
_2009

---

### Post by fjgaude on 2009-04-23
Gosh, I don't have a clue! Could be the drives are actually bad.

Have you tried using one at a time as single drives to see if they act normal?

After you have created an array with **mdadm** you might have to zero the superblocks in each drive to use them as normal devices.

```
sudo mdadm --zero-superblock /dev/sdb1
```

Etc.

---

### Post by _2009 on 2009-04-23
> Have you tried using one at a time as single drives to see if they act normal?

No can do. I've got them online in our server!

I might manually fail /dev/sda to see what happens...

---

### Post by _2009 on 2009-04-23
OK. I set /dev/sda to faulty removed, redefined the partition and added back into the array and now "$ sudo fdisk -l" gives me:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1743ea48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d641cae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d641cae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   fd  Linux raid autodetect

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae980
```

As you can see /dev/sda now has a partition table and unique disk id, but /dev/sdb is now up the spout! What's going on?

I also noticed, which I'd missed before, that on my initial post /dev/sdd also has the same disk id! (I've now highlighted this in green as well.)

---

### Post by fjgaude on 2009-04-23
If you don't have any unbackedup data on them I'd start over. Have you studied things like this link:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Seems something is not normal. If you partitioned each drive, then created the array, then made a filesystem on the array things should be okay. Maybe the controller is bad.

You seem to have drives that have been messed up with **mdadm** and the only way is to start over, IMO. Don't forget the zeroing of each drive's superblock with mdadm.

---

