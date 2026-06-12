---
title: "Can't mount partitions on /dev/hda"
date: 2006-10-03
forum: Desktop Environments
---

### Post by sketerpot on 2006-10-03
I have a secondary hard drive with three partitions, one of which is ext3 and has a bunch of data which I want. I stuck the hard drive into my computer and hooked it up the same way I've hooked it up several times before when the computer was running other OSes, and the computer recognizes the hard drive.

The hard drive has been dubbed "/dev/hda", and when I go to System->Administration->Disks and click on the partitions tab for the hard drive, it shows my three partitions and says that the relevant one, partition 3, is called "/dev/hda3". I've tried to mount this, but the device "/dev/hda3" does not exist.

Anybody know what's going on?

---

### Post by devils_casper on 2006-10-03
in terminal, type 

sudo fdisk -l 

check the output and mount accordingly. if problem persists, post the output of fdisk -l



casper

---

### Post by sketerpot on 2006-10-03
The output of fdisk -l:

```
Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   83  Linux
/dev/hda2               6          68      506047+  83  Linux
/dev/hda3              69        7476    59504760   83  Linux
```

/dev/hda exists, but /dev/hda{1,2,3} do not exist.

---

### Post by cptnapalm on 2006-10-03
I'm a bit confused...

According to your last post, fdisk sees 3 partitions, but you say that hda1, hda2 and hda3 don't exist.  Do you mean that as "but they really don't exist, even though fdisk says they do" or that the output from trying to mount states that they do not exist?

what file systems do each one have?  (Why is the first partition so small?)

how are you mounting it?  sudo mount -t <fs type> /dev/hdaX /mountpoint ?

---

### Post by sketerpot on 2006-10-03
> **cptnapalm said:**
> I'm a bit confused...

According to your last post, fdisk sees 3 partitions, but you say that hda1, hda2 and hda3 don't exist.  Do you mean that as "but they really don't exist, even though fdisk says they do" or that the output from trying to mount states that they do not exist?

They don't really exist, even though fdisk says they do.

```
sketerpot@creideiki:~$ ls /dev/hda*
/dev/hda
```

> what file systems do each one have?  (Why is the first partition so small?)

The first one is ext2 which used to be mounted at /boot on another machine but which I now want to ignore, the second is an old swapfs (which I indend to ignore if at all possible), and the third is the ext3 partition with the data I want.

> how are you mounting it?  sudo mount -t <fs type> /dev/hdaX /mountpoint ?

Yes, exactly that.

---

### Post by sketerpot on 2006-10-04
I've also tried using /dev/MAKEDEV, but it says that it doesn't know how to make /dev/hda3.

---

