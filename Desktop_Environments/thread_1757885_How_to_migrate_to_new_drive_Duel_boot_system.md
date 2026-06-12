---
title: "How to migrate to new drive? Duel boot system"
date: 2011-05-13
forum: Desktop Environments
---

### Post by jamesjenner on 2011-05-13
G'day peoples,

I should warn you straight up that I'm not familiar with how Linux handles disk drives. Just getting that clear before I ask my question (which could come across pretty newbish). 

I've got a NTFS drive on /dev/sda:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS
```

I've installed Ubuntu (10.10, a while ago) on a second drive, on /dev/sdd1 (i presume based on fdisk):

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       59322   476502016   83  Linux
/dev/sdd2           59323       60802    11881473    5  Extended
/dev/sdd5           59323       60802    11881472   82  Linux swap / Solaris
```

I have a couple of other drives, but they're not important right now.

So, what I wish to do is remove my Vista drive, but I presume that grub is on it as I'm duel booting. The reason I wish to remove it is because an old drive of mine failed (it's the same as my Vista/boot drive) and I want to swap the board over to see if I can recover data from it.

So, my question is, can I just remove the first drive and start booting on my Linux partition? Do I need to do anything other than go into the bios and change which SATA drive to boot first?

What info from fdisk can I take to determine the drive in my bios? I have several 1 gig drives and they're all the same manufacturer. Does the Disk identifier some how correlate to the serial number of the drive and if so is as simple as converting from hex to base 10 to determine?

Last question, is there any easy way to create an image of the 500GB drive to I can apply it to another drive if I have a failure? I would rather do that than a backup so I could restore my vista drive if there are any problems (already have a backup, but restoring windows, installing software, etc is such a pain in the ***). 

Hopefully my questions are quite simple, and some guidance in what to use will be enough.

Oh, just in case you need it, here's fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x172859af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa66d8171

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008df7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       59322   476502016   83  Linux
/dev/sdd2           59323       60802    11881473    5  Extended
/dev/sdd5           59323       60802    11881472   82  Linux swap / Solaris
```

---

### Post by wildmanne39 on 2011-05-14
> **jamesjenner said:**
> G'day peoples,

I should warn you straight up that I'm not familiar with how Linux handles disk drives. Just getting that clear before I ask my question (which could come across pretty newbish). 

I've got a NTFS drive on /dev/sda:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS
```

I've installed Ubuntu (10.10, a while ago) on a second drive, on /dev/sdd1 (i presume based on fdisk):

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       59322   476502016   83  Linux
/dev/sdd2           59323       60802    11881473    5  Extended
/dev/sdd5           59323       60802    11881472   82  Linux swap / Solaris
```

I have a couple of other drives, but they're not important right now.

So, what I wish to do is remove my Vista drive, but I presume that grub is on it as I'm duel booting. The reason I wish to remove it is because an old drive of mine failed (it's the same as my Vista/boot drive) and I want to swap the board over to see if I can recover data from it.

So, my question is, can I just remove the first drive and start booting on my Linux partition? Do I need to do anything other than go into the bios and change which SATA drive to boot first?

What info from fdisk can I take to determine the drive in my bios? I have several 1 gig drives and they're all the same manufacturer. Does the Disk identifier some how correlate to the serial number of the drive and if so is as simple as converting from hex to base 10 to determine?

Last question, is there any easy way to create an image of the 500GB drive to I can apply it to another drive if I have a failure? I would rather do that than a backup so I could restore my vista drive if there are any problems (already have a backup, but restoring windows, installing software, etc is such a pain in the ***). 

Hopefully my questions are quite simple, and some guidance in what to use will be enough.

Oh, just in case you need it, here's fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x172859af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa66d8171

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008df7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       59322   476502016   83  Linux
/dev/sdd2           59323       60802    11881473    5  Extended
/dev/sdd5           59323       60802    11881472   82  Linux swap / Solaris
```
Hi, if you go to places in ubuntu you should be able to see the drives you want to get the files from and you can just copy them over to ubuntu while your current windows disk is connected. The windows drive has to be mounted. That is what I did my windows disk was failing so I copied all the files I needed and then I replaced the drive with a new one. I hope this helps.:o

---

### Post by jamesjenner on 2011-05-14
> **wildmanne39 said:**
> Hi, if you go to places in ubuntu you should be able to see the drives you want to get the files from and you can just copy them over to ubuntu while your current windows disk is connected. The windows drive has to be mounted. That is what I did my windows disk was failing so I copied all the files I needed and then I replaced the drive with a new one. I hope this helps.:o

Ahh maybe I wasn't clear. I have two Identical 500GB WD drives. One has failed (the drive is dead, I suspect the electronics. It cannot be mounted, cannot be booted from, etc. possible physical fault on platters but I suspect a fault on the PCB), the other drive is my primary drive which has vista on it and I presume grub as it's the drive I boot from.

I need to remove my current 500GB Vista drive which I boot from so I can remove the PCB from the good drive and put it on the bad drive, in the hopes that I can recover from the bad drive. It is not possible to mount the bad drive under linux or under vista.

So to do this I need to do two things:

[LIST=1]
[*]create an image of my 500GB Vista drive (the current one I'm using, which is a good drive)
[*]Remove the 500GB drive and boot only from Linux (which I'm not sure if it's as simple as changing boot order in bios or if I need to do something else under Ubuntu to let it boot without grub).
[/LIST] 

Hope that clarifies things.

Btw, all drives are SATA.

:edit:

I should note, the reason I wish to take an image from my good drive (the one I currently boot from) is so that if in removing the PCB I damage it, I can apply the image to another drive. Which reminds me, if someone can tell me how to take the image, do they also know if I can apply the image to a drive of a different physical size (bigger that is)?

---

### Post by jamesjenner on 2011-05-14
In my wanderings I've discovered some tools, but I'm not sure how suitable they are for what I wish to do.

The tools are:

[INDENT][PartClone]("http://partclone.org/index.php")
[PartImage]("http://www.partimage.org/Main_Page")
[FS Archiver]("http://www.fsarchiver.org/Main_Page")[/INDENT]

Apparently the first two will create an image and support NTFS and the third one backs up based on the files, not based on used sectors.

I'm kinda confused about backing up the blocks that are used and how they're restored. I'm not sure if they can be restored to a drive that has a different size or if I can create an appropriate partition and write the image to that or if any of them will restore the grub boot loader as well.

The whole point of creating an image is so that I can restore it exactly as is on another drive complete with bootloader (grub) and as such create the least amount of problems, while in the meantime being able to boot to linux while I try and canabalise the working HD to try and recover data from the non functional HD.

Hopefully someone out there has experience with imaging a NTFS drive with grub and/or with changing boot drives.

---

### Post by tnt533 on 2011-05-15
After you remove the windows drive you will have to boot to a live cd and install grub on the Linux drive. Check this out. 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If that tutorial doesn't fit your needs there a thousand others, just do a google for install grub or grub2 depending on what version of Ubuntu you're currently running. Once you reinstall the windows drive you will have to reinstall grub again but this time back on the windows drive using the same methods.  

Good luck.

---

### Post by jamesjenner on 2011-05-15
> **tnt533 said:**
> After you remove the windows drive you will have to boot to a live cd and install grub on the Linux drive. Check this out. 

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If that tutorial doesn't fit your needs there a thousand others, just do a google for install grub or grub2 depending on what version of Ubuntu you're currently running. Once you reinstall the windows drive you will have to reinstall grub again but this time back on the windows drive using the same methods.  

Good luck.

Ahh, thanks mate. This is exactly what I was looking for. I didn't think to google on grub, was googling on migration from duel boot to single boot, which alas resulted in nothing worth while.

Turns out that the imaging issue is now a non-issue as what I thought was a duplicate disk turned out not to be. So no moving the PCB to the broken one. But at least now I can change my system to only boot from Linux.

Again, thanks for your reply.

Cheers,

James.

---

### Post by jamesjenner on 2011-05-17
Opps. removed as I posted in wrong thread. sorry.

---

