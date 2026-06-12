---
title: "How do you find out file system of usb device?"
date: 2009-04-07
forum: General Help
---

### Post by VeryLost on 2009-04-07
Hello all,

   I have an external Hard drive and I am trying to find out what file system it is currently using. I spent some time googling and I found some commands that might do the trick.

fdisk -l (device)

file -s (deive)

The problem is I cannot find what device the disk is. If I go into file browser I can see and navigate the drive. It states that it is located in /media.

However, if I try to execute any of the above commands using /media/SEA_DISK they say no such file or directory.

I tried looking in /dev/ for the device but its all just a bunch non intututive letter and number conventions.

I also looked in lsusb but it did not give me anything that worked with either of the above mentioned commands.

Can anyone please tell me how to figure out what file system my External drive is using.

I know by default its probably using FAT32, but I want to learn how to find this out in linux.

-Thanks

---

### Post by ShaunG on 2009-04-07
run

```
sudo fdisk -l
```

in a command line on its own.

This will give you a listing of all devices and theirs file types among other things. If the device is mounted you can also run

```
mount
```

in a command line to see the name of the mounted usb deviceh. You'll see a lot of stuff but look for the entry that has the mountpoint /media/ in it. 

Compare the output of those two and you'll know. :D

---

### Post by blackgr on 2009-04-07
> **VeryLost said:**
> Hello all,

   I have an external Hard drive and I am trying to find out what file system it is currently using. I spent some time googling and I found some commands that might do the trick.

fdisk -l (device)

file -s (deive)

The problem is I cannot find what device the disk is. If I go into file browser I can see and navigate the drive. It states that it is located in /media.

However, if I try to execute any of the above commands using /media/SEA_DISK they say no such file or directory.

I tried looking in /dev/ for the device but its all just a bunch non intututive letter and number conventions.

I also looked in lsusb but it did not give me anything that worked with either of the above mentioned commands.

Can anyone please tell me how to figure out what file system my External drive is using.

I know by default its probably using FAT32, but I want to learn how to find this out in linux.

-Thanks

Do this
```

mount | grep SEA
```

and then after you determine the device name
```

sudo fdisk -l /dev/sd.....
```


EDIT: just "mount | grep SEA" is enough. You can even type "mount" to see all mounted disks and their filesystems

---

### Post by VeryLost on 2009-04-08
I entered the commands at received this output


> Disk /dev/sdb1: 250.0 GB, 250056705024 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


I booted into windows (I am dual booting) and looked at the drive into in there.

The disk is formatted as NTFS and ubuntu can read and write from it just fine, but for some reason it wont list that its a NTFS file system.

Did I enter a command incorrectly?

-Thanks

---

### Post by aeiah on 2009-04-08
is there a chance your usb drive has some kind of built in encryption or other software that they've implemented? that can often confuse linux.


incidentally, i often find the best way to check what /dev/ name it hasis to do this before plugging it in:
```

cd /dev/
ls sd*

```

and then
```

ls sd*

```
afterwards. its nice and clear and makes it hard to make mistakes.

---

### Post by VeryLost on 2009-04-10
Thats a really neat trick with the ls command.

When I did that after I plugged in the disk I received to additional entries.

sdb and sdb1

If I execute the fdisk -l /dev/sdb1 command I get the error.

However, if I execute fdisk -l /dev/sdb the command works and returns that the disk is formatted as NTFS.

Thanks!

---

