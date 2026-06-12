---
title: "Flash drives now think they belong to root"
date: 2011-05-07
forum: Desktop Environments
---

### Post by peyre on 2011-05-07
Suddenly a couple weeks ago, I found I couldn't copy to my flash drives any more.  Turns out Xubuntu is mounting them as root now, and if I want to write to them, delete from them, or even dismount them, I have to open Thunar or Nautilus as root rather than as myself.  This never happened before.  I can still write to zip disks and other media as before--this only seems to affect flash drives.

I've tried doing a chmod from the command line, but it doesn't work.  I've also tried getting Properties on the flash drive, and changing owners, or changing Other to read & write access.  It won't let me change ownership, and while it will let me change Other to read+write, the change doesn't stick--when I open Properties again, it's back to read-only.

This happened while I was still on 10.10.  I didn't complain about this at first, figuring the 11.04 upgrade might fix it--but no such luck.  The only thing I can think of that might have prompted it was that I installed MountManager about that time.  Removing it didn't help, FWIW.

---

### Post by Copper Bezel on 2011-05-08
What filesystem format are the flash drives using? If they're FAT32, they don't store permissions, and you can get some unpredictable behavior.

I know there's an unrelated problem with flash drives mounting as read only, which I think can be fixed by editing fstab, but that's a bit of a mess (and I don't think it's the cause in this case.)

---

### Post by peyre on 2011-05-08
> **Copper Bezel said:**
> What filesystem format are the flash drives using? If they're FAT32, they don't store permissions, and you can get some unpredictable behavior.

Well, one's formatted FAT16, one's FAT32, and the other's NTFS.  They all behave the same way.

---

### Post by ottosykora on 2011-05-08
I experienced the same. On 10.04, fat32 drives were read/write, as from 10.10 they are read only. Tried lot of advise fomr the forum, no help to it so far. End of using usb sticks on linux apparently.

---

### Post by Toz on 2011-05-08
Sometimes these kinds of problems are caused by filesystem errors on the device itself. Try running:```
sudo dosfsck /dev/xxx
```
(where xxx is the device name of the memory stick)

to see if it reports any errors.

---

### Post by peyre on 2011-05-08
It errors out, saying it's a directory.

---

### Post by Toz on 2011-05-08
Can you show the output of the command?

---

### Post by peyre on 2011-05-08
Sure:
```
leon@peyre:~$ sudo dosfsck /dev/usb0
[sudo] password for leon: 
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
open: No such file or directory

```

---

### Post by Toz on 2011-05-09
Plug in the usb key then open a terminal and type in```
dmesg
```. Reply back with the last 10 lines or so.

---

### Post by peyre on 2011-05-09
Here you go (and then some):

```
[339969.453408] usb 1-2: new high speed USB device using ehci_hcd and address 16
[339969.595459] scsi15 : usb-storage 1-2:1.0
[339970.605037] scsi 15:0:0:0: Direct-Access     LEXAR    JUMPDRIVE SECURE 1000 PQ: 0 ANSI: 0 CCS
[339970.605524] sd 15:0:0:0: Attached scsi generic sg7 type 0
[339970.607263] sd 15:0:0:0: [sdg] 2026592 512-byte logical blocks: (1.03 GB/989 MiB)
[339970.608084] sd 15:0:0:0: [sdg] Write Protect is off
[339970.608087] sd 15:0:0:0: [sdg] Mode Sense: 43 00 00 00
[339970.609384] sd 15:0:0:0: [sdg] No Caching mode page present
[339970.609388] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[339970.613014] sd 15:0:0:0: [sdg] No Caching mode page present
[339970.613018] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[339970.657506]  sdg: sdg1
[339970.660767] sd 15:0:0:0: [sdg] No Caching mode page present
[339970.660772] sd 15:0:0:0: [sdg] Assuming drive cache: write through
[339970.660775] sd 15:0:0:0: [sdg] Attached SCSI disk
[470601.447466] chrome[17264]: segfault at d2850094 ip 014d4b4b sp bf9e1674 error 5 in libgcflashplayer.so[ed3000+bc6000]
[501866.801363] internal-queue:[5678]: segfault at 0 ip 45ae3377 sp ab6f46e0 error 4 in libgstbase-0.10.so.0.28.0[45ac1000+3f000]

```

---

### Post by Toz on 2011-05-09
Try:```
sudo dosfsck /dev/sdg1
```
Remember to back up your data before you do - just in case.

---

### Post by peyre on 2011-05-09
Interesting!

```
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action

```
...continued...
```
? 2
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP362/change.log.1
  File size is 372 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 372 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP367/CHANGE.LOG
  File size is 2248 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 2248 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP370/change.log.1
  File size is 412 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 412 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP370/CHANGE.LOG
  File size is 438 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 438 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP374/change.log.1
  File size is 382 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 382 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP374/change.log.2
  File size is 3212 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 3212 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP377/CHANGE.LOG
  File size is 3154 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 3154 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP380/CHANGE.LOG
  File size is 392 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 392 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP381/CHANGE.LOG
  File size is 67404 bytes, cluster chain length is > 69632 bytes.
  Truncating file to 67404 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP406/CHANGE.LOG
  File size is 656 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 656 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP410/CHANGE.LOG
  File size is 5780 bytes, cluster chain length is > 8192 bytes.
  Truncating file to 5780 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP412/CHANGE.LOG
  File size is 358 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 358 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP413/CHANGE.LOG
  File size is 696 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 696 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP419/CHANGE.LOG
  File size is 388 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 388 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP199/CHANGE.LOG
  File size is 540 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 540 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.1
  File size is 368 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 368 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.2
  File size is 370 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 370 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.3
  File size is 378 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 378 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.4
  File size is 542 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 542 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/CHANGE.LOG
  File size is 384 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 384 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.1
  File size is 394 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 394 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.2
  File size is 396 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 396 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.3
  File size is 404 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 404 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/CHANGE.LOG
  File size is 806 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 806 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP28/CHANGE.LOG
  File size is 468 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 468 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP29/change.log.1
  File size is 386 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 386 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP29/CHANGE.LOG
  File size is 364 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 364 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP30/CHANGE.LOG
  File size is 444 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 444 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP34/CHANGE.LOG
  File size is 1534 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 1534 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP95/CHANGE.LOG
  File size is 366 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 366 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP96/change.log.1
  File size is 482 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 482 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP96/CHANGE.LOG
  File size is 1994 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 1994 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP98/CHANGE.LOG
  File size is 766 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 766 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP115/CHANGE.LOG
  File size is 588 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 588 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP185/CHANGE.LOG
  File size is 520 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 520 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP206/CHANGE.LOG
  File size is 450 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 450 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP266/CHANGE.LOG
  File size is 594 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 594 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP310/CHANGE.LOG
  File size is 400 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 400 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP323/CHANGE.LOG
  File size is 358 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 358 bytes.
/System Volume Information/_restore{83BE25CE-CF1F-4EE7-A83E-5EE431814AD3}/RP15/change.log.1
  File size is 806 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 806 bytes.
/System Volume Information/_restore{A99AF7D1-7953-4534-9301-853570FEAC09}/RP1/CHANGE.LOG
  File size is 982 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 982 bytes.
/System Volume Information/_restore{04AC4467-77CD-4A67-BB5E-AF2D33303B38}/RP80/CHANGE.LOG
  File size is 406 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 406 bytes.
Reclaimed 4 unused clusters (16384 bytes).
Free cluster summary wrong (113491 vs. really 113620)
1) Correct
2) Don't correct
? 1
Leaving file system unchanged.
/dev/sdg1: 729 files, 138897/252517 clusters

```

But - It's still read-only.

---

### Post by peyre on 2011-05-09
Another thing I've noticed: when I open my flash drive from Places, it opens in /media/usb0 instead of the special thing it used to do, where on the left I just saw the flash drive's label.

As you can see in the attached, it's opened to usb0.  The drive's label, LEXAR, still shows on the left, but if I click on it nothing happens.  (I mean that if I click on something else I see the contents of what I clicked on.  But then when I click on LEXAR, the panel on the right still shows the contents of what I had clicked on before.)

---

### Post by Toz on 2011-05-10
okay then, lets trying repairing it:```
sudo dosfsck -a /dev/sdg1
```
Remember to back up any important data you may have.

---

### Post by peyre on 2011-05-10
```
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP362/change.log.1
  File size is 372 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 372 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP367/CHANGE.LOG
  File size is 2248 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 2248 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP370/change.log.1
  File size is 412 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 412 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP370/CHANGE.LOG
  File size is 438 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 438 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP374/change.log.1
  File size is 382 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 382 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP374/change.log.2
  File size is 3212 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 3212 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP377/CHANGE.LOG
  File size is 3154 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 3154 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP380/CHANGE.LOG
  File size is 392 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 392 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP381/CHANGE.LOG
  File size is 67404 bytes, cluster chain length is > 69632 bytes.
  Truncating file to 67404 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP406/CHANGE.LOG
  File size is 656 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 656 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP410/CHANGE.LOG
  File size is 5780 bytes, cluster chain length is > 8192 bytes.
  Truncating file to 5780 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP412/CHANGE.LOG
  File size is 358 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 358 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP413/CHANGE.LOG
  File size is 696 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 696 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP419/CHANGE.LOG
  File size is 388 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 388 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP199/CHANGE.LOG
  File size is 540 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 540 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.1
  File size is 368 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 368 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.2
  File size is 370 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 370 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.3
  File size is 378 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 378 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/change.log.4
  File size is 542 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 542 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP439/CHANGE.LOG
  File size is 384 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 384 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.1
  File size is 394 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 394 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.2
  File size is 396 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 396 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/change.log.3
  File size is 404 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 404 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP200/CHANGE.LOG
  File size is 806 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 806 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP28/CHANGE.LOG
  File size is 468 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 468 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP29/change.log.1
  File size is 386 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 386 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP29/CHANGE.LOG
  File size is 364 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 364 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP30/CHANGE.LOG
  File size is 444 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 444 bytes.
/System Volume Information/_restore{C9BE5FF6-5D81-4865-93F6-23230121CB28}/RP34/CHANGE.LOG
  File size is 1534 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 1534 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP95/CHANGE.LOG
  File size is 366 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 366 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP96/change.log.1
  File size is 482 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 482 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP96/CHANGE.LOG
  File size is 1994 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 1994 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP98/CHANGE.LOG
  File size is 766 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 766 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP115/CHANGE.LOG
  File size is 588 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 588 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP185/CHANGE.LOG
  File size is 520 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 520 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP206/CHANGE.LOG
  File size is 450 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 450 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP266/CHANGE.LOG
  File size is 594 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 594 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP310/CHANGE.LOG
  File size is 400 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 400 bytes.
/System Volume Information/_restore{01A7EB2E-A525-4B5C-9C39-5178F150FEAA}/RP323/CHANGE.LOG
  File size is 358 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 358 bytes.
/System Volume Information/_restore{83BE25CE-CF1F-4EE7-A83E-5EE431814AD3}/RP15/change.log.1
  File size is 806 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 806 bytes.
/System Volume Information/_restore{A99AF7D1-7953-4534-9301-853570FEAC09}/RP1/CHANGE.LOG
  File size is 982 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 982 bytes.
/System Volume Information/_restore{04AC4467-77CD-4A67-BB5E-AF2D33303B38}/RP80/CHANGE.LOG
  File size is 406 bytes, cluster chain length is > 4096 bytes.
  Truncating file to 406 bytes.
Reclaimed 4 unused clusters (16384 bytes) in 1 chain.
Free cluster summary wrong (113491 vs. really 113616)
  Auto-correcting.
Performing changes.
/dev/sdg1: 730 files, 138901/252517 clusters

```

Of course, it's still read-only.  I could just format this thing and then try with a fresh file system.

---

### Post by Toz on 2011-05-10
Hmmmm, interesting.

Do you have usbmount installed? From a terminal:```
apt-cache policy usbmount
```

If so, try removing it:```
sudo apt-get remove usbmount
```

Note: Just read up on usbmount```
apt-cache show usbmount
``` and it appears to be whats creating the /media/usb0 mount points. I don't have it installed and have no problems with mounting/reading usb drives.

---

### Post by peyre on 2011-05-11
Dang!  Looks like that did the trick.  Thanks Toz!!

---

