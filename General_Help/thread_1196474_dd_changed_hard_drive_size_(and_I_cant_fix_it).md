---
title: "dd changed hard drive size (and I cant fix it)"
date: 2009-06-25
forum: General Help
---

### Post by piratebill on 2009-06-25
Ok I have a really odd issue here. My friend was running out of HD space and asked me to clone their old laptop drive (running XP) to newer, larger drive. I used dd to copy the drive


```
sudo dd if=/dev/sdb of=/dev/sdc
```

It did clone successfully, but it kept the partition to 38 gigs. I then used Gparted to resize the ntfs partition to fill the rest of the drive. It gave me the bluescreen of death upon booting. We then decided it would be easier to reload windows from scratch (this is where the weird part happens).

The Xp cd only sees the new drive to be capable of holding 38 gigs. However, gparted still sees the drive is 120 gigs. If I format the drive with gparted, windows still wont recognize more than 38 gigs (tried with two computers). I figured that dd changed some table that windows reads, but linux ignores so I ran this:


```
sudo dd if=/dev/zero of=/dev/sdb
```

to zero out the drive, but the problem persists.

I am very stumped here. the last idea I have is to get an old drive of mine, format it to use 120 gigs and dd that to the new one, but this will take a lot more time than I have left to give. Do any of you know what is going on with this hard drive?



UPDATE:
I formated the drive using gparted (120 gig partition) and had fdisk varify the partition. It said


```
total allocated sectors 234436483 greater than the maximum 75200265
```

I know that is not a standard message. Any ideas at all?  Also, gparted only sees the drive as 120 gigs from a boot cd, not from my actual system


UPDATE II:
The cylinder count, head count and sector per track count are not what they should be. By googling the drive, I found it should be 16383/16/63. I tried changing these values in fdisk, but no luck. How can I change these values so that they stick? I think that would fix everything.


Do you think I did this by messing up some dd command, or is the drive just fraked?


UPDATE III:

Just ran hdparm -g to get the cylinder/head count for the new drive and the old, they were different so I think I can safely say dd didn't cause this.  Please, any ideas would be awesome.

---

### Post by piratebill on 2009-06-25
bump

---

### Post by mk1w86 on 2009-06-25
I don't know if this will work but you could try dban which should fully erase every part of the drive.

[http://www.dban.org/](http://www.dban.org/)

---

### Post by geirha on 2009-06-25
I believe the MBR does contain the number of cylinders and sectors of the drive, set by whichever partitioner partitioned it. So I do believe this use of dd is the problem, since you are also copying the MBR (first 512 bytes of the drive)

I'd try wiping the MBR on your new drive. ```
sudo dd if=/dev/zero bs=512 count=1 of=/dev/sdb
```
Then use fdisk (or gparted if you're not comfortable with fdisk) on the drive and create partitions equal to the old drive. Fdisk/gparted should also set the hard drive size properly.
```
sudo fdisk /dev/sdb
```
Fdisk is not too hard to use. Start off by typing **m** to see the available commands, and use **p** to view the partition table after each change you make. Nothing will actually be written to the disk before you run the **w** command.

The partitions will need to be either the same size or larger. Make them slightly larger to be on the safe side. Also make sure the active flag (fdisk calls this "bootable flag") is set on the right partition.

Then, copy each partition individually.
```
sudo dd if=/dev/sda1 of=/dev/sdb1
sudo dd if=/dev/sda2 of=/dev/sdb2
# etc...

```

Lastly, you'll need to (re)install the boot loader on the new drive. I believe you do that by booting the XP cd and run a command like "fixmbr" (my knowledge of XP is limited, so verify with google)

---

### Post by piratebill on 2009-06-25
Thanks geirha.  I cant actually do any of that now (on break at work), but I think dd =if/dev/zero of=/dev/sda wiped the whole drive (mbr included.  Please correct me if I am wrong).  But if it didn't I know I have used fdisk to clear the mbr (and a windows disk to recreate it).  My coworkers seem to think the logic board is just messed up.  Any thoughts?

---

### Post by dcstar on 2009-06-26
> **piratebill said:**
> Thanks geirha.  I cant actually do any of that now (on break at work), but I think dd =if/dev/zero of=/dev/sda wiped the whole drive (mbr included.  Please correct me if I am wrong).  But if it didn't I know I have used fdisk to clear the mbr (and a windows disk to recreate it).  My coworkers seem to think the logic board is just messed up.  Any thoughts?

Use the Partition Editor to create a new Partition Table onto the new drive, use the Partition Editor to Copy the old partition to the new drive.

Use a Windows tool to put a new Windows MBR on the new drive.

---

### Post by piratebill on 2009-06-27
geirha, you are correct. DD is the problem.  I just got a new drive today (thinking the old one was faulty.  Before dd-ing it I checked the size and was out of the box 250 Gb.  Ran DD again, cloned the drive, and now the drive only reads as 38 Gb.  I used the command you gave me to wipe out the MBR; no effect.  I am D-banning the drive now as a last ditch effort.  Please, any more help would be amazing.

---

### Post by drs305 on 2009-06-27
I don't use dd so I don't know if this applies, but if you clone a drive with partimage or similar software to a larger partition, an ext2 or 3 partition will indicate the cloned size until you run "resize2fs" or something that does the same thing.

---

### Post by piratebill on 2009-06-27
I found the solution!  Here
[http://www.technologyquestions.com/technology/linux/225913-recover-hd-size-after-dd-command.html](http://www.technologyquestions.com/technology/linux/225913-recover-hd-size-after-dd-command.html)

There is a program called hdat2 that will allow you to "set max address."  It detected the drive was a 250Gb and only registered as a 38Gb.  Fixed it really quick.

---

