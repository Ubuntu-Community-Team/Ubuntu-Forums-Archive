---
title: "Gparted can't format Microsd Card"
date: 2009-03-10
forum: General Help
---

### Post by Dizzzzzzid on 2009-03-10
Ok so I've been messing around with my G1 and microsd card and whatever. I kept running into the problem of my sdcard randomly becoming read-only, while this sucked a lot, I could just reformat since nothing to valuable was on it(brand new). Until today when trying to do it the partion on it comes up as "unknown" so that when i try to format it I get this

> GParted 0.3.8

Libparted 1.8.9

Format /dev/sdc1 as fat32  00:00:01    ( ERROR )
     	
calibrate /dev/sdc1  00:00:01    ( SUCCESS )
     	
path: /dev/sdc1
start: 16065
end: 7743329
size: 7727265 (3.68 GiB)
set partitiontype on /dev/sdc1  00:00:00    ( ERROR )
libparted messages    ( INFO )
     	
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Can't write to /dev/sdc, because it is opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.
Can't write to /dev/sdc, because it is opened read-only.
Unable to open /dev/sdc read-write (Read-only file system). /dev/sdc has been opened read-only.

When mounting I get the output: 

> mount: block device /dev/sdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




I'm just at a loss for what to do. Usually I can find answers to problems through google and these forums but nothing is really working. Thanks in advanced.

---

### Post by Yellow Pasque on 2009-03-10
What kind of filesystem is currently on it? NTFS?
```
sudo fdisk -l
```

---

### Post by warp99 on 2009-03-10
You can repartition the card using fdisk, then reformat using mkfs.msdos. First insert the card and make sure the device (/dev/sdc) has not changed terminals. Then issue the following:

```
sudo fdisk /dev/sdc
```

Press m for the command list, then delete the first partition.
Press n for a new partition, choose primary partition, accept the defaults
Press t for type to change system id, then press c for FAT32 (LBA)
Press p to print and verify everything is correct then w to write the data.

Pull the drive, wait a few seconds, then insert the drive again.

Check the terminal location of the drive again (/dev/sdc). If the file system becomes mounted by udev then unmount the device and issue the following:
```
sudo mkfs.msdos -F 32 /dev/sdc1
```

You should be back to your original point on the drive.

---

### Post by Dizzzzzzid on 2009-03-11
The output from fdisk -l is 

> Disk /dev/sdc: 3965 MB, 3965714432 bytes
255 heads, 63 sectors/track, 482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0238

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2         482     3863632+   b  W95 FAT32


And I'm doing Warp's sugestion right now....

---

### Post by Dizzzzzzid on 2009-03-11
ok so I tried both Warp and this is the output before I even tried to do anything in fdisk
> sudo fdisk /dev/sdc
You will not be able to write the partition table.


and after I tried to write the changes

> Unable to write /dev/sdc

shocker

and mkfs came out with

> mkfs.msdos: unable to open /dev/sdc

---

### Post by Neo_The_User on 2009-03-11
sudo dd if=/dev/zero of=/dev/sdc bs=512

there. do that from ubuntu livecd in terminal. NOBODY ELSE TRY THAT!!!!!!!!! it'll take an hour or so and you won't see any output from the terminal from quiet some time. good luck.

---

### Post by dcstar on 2009-03-11
> **Dizzzzzzid said:**
> Ok so I've been messing around with my G1 and microsd card and whatever. **I kept running into the problem of my sdcard randomly becoming read-only**, while this sucked a lot, I could just reformat since nothing to valuable was on it(brand new).
........
I'm just at a loss for what to do. Usually I can find answers to problems through google and these forums but nothing is really working. Thanks in advanced.

SSD devices have a finite life before they die - continually reformatting them just brings their demise closer, it seems that this one has died already.

---

### Post by Dizzzzzzid on 2009-03-11
> **Neo_The_User said:**
> sudo dd if=/dev/zero of=/dev/sdc bs=512

there. do that from ubuntu livecd in terminal. NOBODY ELSE TRY THAT!!!!!!!!! it'll take an hour or so and you won't see any output from the terminal from quiet some time. good luck.
Alright I can do that, must be from a live cd? And just wondering what it does

And dcstar, could it really have died that quick? Would I be better off just returning it?

---

### Post by Neo_The_User on 2009-03-11
It will delete every block of data on that hard drive 1 by 1, bit by bit. Yes has to be done from livecd. The theory of that command will set every block to 0 therefor completley blanking it out. It'll nuke the hard drive. WILL NOT BREAK!

---

### Post by Dizzzzzzid on 2009-03-11
> **Neo_The_User said:**
> It will delete every block of data on that hard drive 1 by 1, bit by bit. Yes has to be done from livecd. The theory of that command will set every block to 0 therefor completley blanking it out. It'll nuke the hard drive. WILL NOT BREAK!
Alright, thanks a lot. I appreciate it.

---

### Post by Neo_The_User on 2009-03-11
> **Dizzzzzzid said:**
> Alright, thanks a lot. I appreciate it.

np

---

### Post by Dizzzzzzid on 2009-03-11
> **Neo_The_User said:**
> sudo dd if=/dev/zero of=/dev/sdc bs=512

there. do that from ubuntu livecd in terminal. NOBODY ELSE TRY THAT!!!!!!!!! it'll take an hour or so and you won't see any output from the terminal from quiet some time. good luck.

Ok so when I tried that it gave me the error

> dd: opening '/dev/sdb1': Read-only file system

P.S sdb1 is what it came up as in the live cd

---

### Post by taihlo on 2009-08-25
I am having a similar problem with a software encrypted USB drive.  I have tried everything (sadly including windows) still getting stuck on the "Read-only file system" issue

---

### Post by Mortesins93 on 2011-02-14
I had the same problem, after trying everything (including windows, sadly), I found out that on the left side of the SD card (which works as an adapter) there is a small thingy with "lock" written next to it. When this thing is on the lock position (pulled down), the filesystem becomes a read only.

---

### Post by lava on 2011-06-07
> **Mortesins93 said:**
> I had the same problem, after trying everything (including windows, sadly), I found out that on the left side of the SD card (which works as an adapter) there is a small thingy with "lock" written next to it. When this thing is on the lock position (pulled down), the filesystem becomes a read only.

Haha, thanks for that tip. I was searching high and low for a solution for my problem. I have a micro SD card I was trying to fix, and after I read your comment I realized that the microSD adapter was locked.

---

### Post by Mortesins93 on 2011-06-08
Always happy to help

---

