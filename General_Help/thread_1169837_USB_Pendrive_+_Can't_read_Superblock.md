---
title: "USB Pendrive + Can't read Superblock"
date: 2009-05-25
forum: General Help
---

### Post by rauldinho on 2009-05-25
Hi, i am having problems mounting a pendrive in my PC running Ubuntu 9.04. When i plug the device it shows me a message windows saying that it cannot mount the device because it *can't read the superblock*, and when i execute *dmesg* this is what it shows:

```
[  888.660268] usb 1-4: new high speed USB device using ehci_hcd and address 6
[  888.794320] usb 1-4: configuration #1 chosen from 1 choice
[  888.804546] scsi8 : SCSI emulation for USB Mass Storage devices
[  888.809036] usb-storage: device found at 6
[  888.809038] usb-storage: waiting for device to settle before scanning
[  893.808256] usb-storage: device scan complete
[  893.808747] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  894.412899] sd 8:0:0:0: [sdb] 7936000 512-byte hardware sectors: (4.06 GB/3.78 GiB)
[  894.413389] sd 8:0:0:0: [sdb] Write Protect is off
[  894.413392] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  894.413394] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  894.414894] sd 8:0:0:0: [sdb] 7936000 512-byte hardware sectors: (4.06 GB/3.78 GiB)
[  894.415389] sd 8:0:0:0: [sdb] Write Protect is off
[  894.415392] sd 8:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  894.415394] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[  894.415398]  sdb: sdb1
[  894.463577] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[  894.463654] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  895.291197] FAT: Filesystem panic (dev sdb1)
[  895.291200]     invalid access to FAT (entry 0x0fae74f8)
[  895.291203]     File system has been set read-only

```

Also when i try a *sudo mount /dev/sdb1/ /mnt/* it tells me the same thing, that i cannot read the superblock. Can anyone tell me if this can be fixed? Thanks in advanced for any answer i may get. Thanks!

---

### Post by KhurramM on 2009-05-26
try to do fsck /dev/whatever for ext3

if it is FAT32 format, then use:
sudo /sbin/dosfsck -altrvV /dev/whatever

See if this can help.

Or else for FAT32, login to windows and scandisk or defrag disk

Hope this helps.

There can also be hardware issue.

---

### Post by rauldinho on 2009-05-26
Hi, i recovered all my data and got my pendrive working again using this command in case someone else has the same problem. Thanks for the help!

```
fsck.vfat -tr /dev/sdb1
```

PD: My device was SDB1.

---

### Post by Martyn Thompson on 2009-09-24
Cheers pal - this has helped me out tonight after I was messing about (read: breaking) my late fathers Matsui MAT 105 MR MP3 player.

---

### Post by SR_ELPIRATA on 2009-10-25
I'm having a problem with my whatever pen drives or similar SD cards. It automounts them in read-only and no matter what I try I can't fix it. Tried using gparted and all the time it reverts to a drive is read-only, but the SD card for example doesnt have its read-only tab set.

Tried the above stated command and I got this:

```
elpirata@htpc:~$ fsck.vfat -tr /dev/sdb
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
open /dev/sdb:Permission denied
elpirata@htpc:~$ sudo fsck.vfat -tr /dev/sdb
[sudo] password for elpirata: 
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
open /dev/sdb:Read-only file system

```

As you can see I also tried with sudo :( Any help? Whenever I plug my 2gb mp3 cheapo player also I cannot delete stuff out of it and weirdly... I can send stuff there, you can see directories and 'files' but the player doesnt recognize them even if they are in the right format (wma/mp3 only). Whenever I try to delete something or try to delete the partitions and start over I get the same 'read-only' messages and can't do a thing.

I'm using 9.04.

ELP

---

### Post by Ubuntist on 2009-11-04
Bump.

I've got a similar problem, except that I am trying to erase a memory stick on which I loaded a 9.04 ISO image.

When I run fsck.vfat on /dev/sdb1, it finds and corrects some problems, but the stick remains read-only.

When I run fsck.vfat on /dev/sdb, it says "Currently only 1 or 2 FATs are supported, not 192".

---

### Post by Naved on 2010-12-25
> **rauldinho said:**
> Hi, i recovered all my data and got my pendrive working again using this command in case someone else has the same problem. Thanks for the help!

```
fsck.vfat -tr /dev/sdb1
```

PD: My device was SDB1.

This shows the error : 'Permissions denied'

---

### Post by greenblob on 2011-09-08
> **Naved said:**
> This shows the error : 'Permissions denied'
```
sudo fsck.vfat -tr /dev/sdb1
(enter password)
```

---

### Post by greenblob on 2011-09-08
I've tried all of the commands above on a 16GB SD card through a card reder on dev/sdb1/ all to no avail. "fsck.vfat -tr /dev/sdb1" just leaves my terminal frozen trying to truncate a bad cluster (7/9 are bad).

_I DON'T CARE IF I HAVE TO FORMAT MY SD CARD, PLEASE CAN SOMEONE JUST GIVE ME A WAY TO FIX IT!!!_

[B]how would I format it through the terminal please?
It is at dev/sdb1/[/B]

---

