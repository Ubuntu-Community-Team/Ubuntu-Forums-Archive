---
title: "Recover NTFS from Ext3?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Huehuecoyotl on 2006-09-18
So. I screwed up.
On my desktop, I had an **80 Gig** (Master) and a **300 Gig drive** (Slave). Before installing Ubuntu, I had a stripped Windows XP operating system on the 300G (for SP2, since the drive was unrecognized under my initial Windows XP installation on the 80G). 

Installed Ubuntu. GRUB did not detect the other drive's OS. 
All my attempts at this failed, I finally resorted to fixboot (or somesuch)

And destroyed all partitions on the drive.
It is not, however formatted.

Is there ANY way I can use Ubuntu on the seperate 80G drive to recover the data still on the partitionless 300G?

---

### Post by aysiu on 2006-09-18
If you didn't actually erase the 300 GB drive, you can mount it and recover the files, yes.

Assuming your master drive is /dev/hda1 and NTFS (type *sudo fdisk -l* in the terminal to be sure): ```
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
``` If it's FAT32 instead, we'll have to adjust the mount command.

---

### Post by Huehuecoyotl on 2006-09-18
silo@SILO-347:~$ sudo mount -t ntfs /dev/hdd /media/recovery -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The physical disk shows up in Disk manager as "/hdd". There are no partitions so there is no "hdd1", etc.

I did not format the drive. The data is still there.

---

### Post by aysiu on 2006-09-18
Even if it's a separate physical drive, it should still have a number. You need a number like /dev/hdd1 or /dev/hdd2.

Can you post the output of this command? ```
sudo fdisk -l
``` That's a lowercase *L*, by the way, not a capital *i*.

---

### Post by Huehuecoyotl on 2006-09-19
(I'm on my laptop at the moment. Class. I'll edit with more complete information later.)

I can tell you the output off the top of my head.

"hdc" and its numbers display properly, that being the 80G drive. If I remember right, there's only one partition and the swap, but there's three entries. May be wrong.

For the next header, which should be the 300G drive, it displays the initial information (everything above " Device Boot", etc). but nothing else. Below is completely blank.

EDIT: Here.
Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9777    78533721   83  Linux
/dev/hdc2            9778        9964     1502077+   5  Extended
/dev/hdc5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/hdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
silo@SILO-347:~$

```

---

### Post by aysiu on 2006-09-19
It looks as if something happened to the partition table for /dev/hdd

There is usually some kind of breakdown, even if it lists only one item--/dev/hdd1

---

### Post by Huehuecoyotl on 2006-09-19
> **aysiu said:**
> It looks as if something happened to the partition table for /dev/hdd

There is usually some kind of breakdown, even if it lists only one item--/dev/hdd1

Yes. That's what I was trying to say earlier. :)
There are no partitions on the 300G drive. Not just one--none. 

It happened when trying to restore Windows XP bootup (NTLDR Missing). My stupidness managed to erase the partition table for it. : /

---

### Post by aysiu on 2006-09-19
I know nothing about how to use this program, but there's something called GPart that supposedly helps you recover lost partition tables.
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

---

### Post by Huehuecoyotl on 2006-09-19
I'll look into it. Thank you :)

If all else fails, I see I can use sudo fdisk /dev/hdd (then "o") to create an empty DOS partition table. Would this overwrite data?

---

### Post by aysiu on 2006-09-19
I believe that would overwrite the data.

---

### Post by Huehuecoyotl on 2006-09-19
Okay. Gparted install. I think all I need to do is create a new partition (since it's labeled as 279 gigs of unallocated space, 'used' and 'free' are N/A). It seems to be the only option, but I can't seem to find a guide to verify that as the correct choice.

EDIT: Apparently Gparted is incompatible with NTFS. Lovely.

---

### Post by aysiu on 2006-09-19
GParted is not incompatible with NTFS.

In any case, the program you want is GPart, not GParted.

---

### Post by Huehuecoyotl on 2006-09-19
Sorry. My bad.

Gpart output is as such:
```

silo@SILO-347:~$ sudo gpart /dev/hdd -v

dev(/dev/hdd) mss(512) chs(36481/255/63)(LBA) #s(586067265) size(286165mb)
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


Begin scan...

```

It's correct in that there used to be four partitions on the drive, but that's it.

---

