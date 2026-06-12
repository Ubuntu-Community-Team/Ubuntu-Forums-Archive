---
title: "How do I mount internal partitions?"
date: 2009-05-25
forum: General Help
---

### Post by Bruce M. on 2009-05-25
Hi folks,

How do I "automatically" mount on boot with read/write permission /dev/sda6, /dev/sda7, /dev/sda9 & /dev/sda10


**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=bc5d0532-a9c0-4f79-820b-04e166333f29  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=6cbddd2d-98bd-4fc1-aab7-e16c8fe5bc85  /home          ext3         relatime                    0  2  
# /dev/sda8
UUID=62ee39a8-d250-44f8-85be-f91fa5764f01  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
```


**fdisl -l**
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000349af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       30401   224660992+   5  Extended
/dev/sda5            2433        7295    39062016   83  Linux
/dev/sda6            7296        9727    19535008+  83  Linux
/dev/sda7            9728       14590    39062016   83  Linux
/dev/sda8           14591       14833     1951866   82  Linux swap / Solaris
/dev/sda9           14834       22617    62524948+  83  Linux
/dev/sda10          22618       30401    62524948+  83  Linux
```

**blkid**
```
/dev/sda10: UUID="84a9c7dd-5473-49f2-89c4-969e03bc99d5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="bc5d0532-a9c0-4f79-820b-04e166333f29" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda1: UUID="bc5d0532-a9c0-4f79-820b-04e166333f29" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="6cbddd2d-98bd-4fc1-aab7-e16c8fe5bc85" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="c7d95158-1929-423d-b5dc-e53735e8bd9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="99e2661c-648e-4449-9907-1f5694611cf1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="62ee39a8-d250-44f8-85be-f91fa5764f01" 
/dev/sda9: UUID="bc8f0137-8bd4-40c8-9cb3-d0ec76e418d5" SEC_TYPE="ext2" TYPE="ext3"
```

And while I'm at it why does blkid report:
```
/dev/sdb1: UUID="bc5d0532-a9c0-4f79-820b-04e166333f29" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda1: UUID="bc5d0532-a9c0-4f79-820b-04e166333f29" SEC_TYPE="ext2" TYPE="ext3" 
```
when **I have NO /dev/sdb1** ?

Thanks have a nice day.
Bruce

---

### Post by taurus on 2009-05-25
What are in /dev/sda6, /dev/sda7, /dev/sda9, & /dev/sda10?

If you want to mount those partitions, edit /etc/fstab and add these lines to the end of it.

```

UUID=c7d95158-1929-423d-b5dc-e53735e8bd9d   /media/sda6   ext3   relatime   0   2
UUID=99e2661c-648e-4449-9907-1f5694611cf1   /media/sda7   ext3   relatime   0   2
UUID=bc8f0137-8bd4-40c8-9cb3-d0ec76e418d5   /media/sda9   ext3   relatime   0   2
UUID=84a9c7dd-5473-49f2-89c4-969e03bc99d5   /media/sda10   ext3   relatime   0   2

```
Save the changes.  Then, create those four new mount points and mount them.

```
sudo mkdir /media/sda6 /media/sda7 /media/sda9 /media/sda10
sudo mount -a
df -h
```
And if you want to write to them, you need to change the ownership of those new mount points from root to your login name, e.g.

```
sudo chown -R username:username /media/sda6
```

Didn't you plug in an external harddrive or thumbdrive to your machine any time before--/dev/sdb1?

---

### Post by rocky5051 on 2009-05-25
I can't answer your last question, but to get a partition to mount at boot you can add them to fstab with a list of other drives to be booted up. Pretend you had the following partition in this example, and the partition is ext3 and you want it to allow executable files, read and write permissions, all that good stuff, you'd add this line for said partition to the fstab like this:

```
sudo gedit /etc/fstab && /dev/hdd1 /mnt/hdd1 ext3 auto,users,exec,rw
```

Just don't erase anything and you'll be fine. Partition format types are named the same as they are when you use mount -t. Like, if you wanted to have an ntfs formatted partition mount at boot time, you would name the type ntfs-3g like you would in mount.

EDIT: I seem to have posted just a moment too late (was typing, lol). His instructions are better.

---

### Post by Bruce M. on 2009-05-25
> **taurus said:**
> What are in /dev/sda6, /dev/sda7, /dev/sda9, & /dev/sda10?

Nothing, they are empty.

Thanks for the help here.

> **taurus said:**
> Didn't you plug in an external harddrive or thumbdrive to your machine any time before--/dev/sdb1?

AaaaaaHA! YES! It was my old 80G drive. My Disk Controller IDE1 died, so I got a SATA WD250G drive and put that in with the 80G drive in the IDE2 Controller to get my personal stuff off it. It is not connected now and has been wiped.

Any way to let Ubuntu (blkid) know that?

**[COLOR="Blue"]EDIT:[/COLOR]** found it:
```
sudo blkid -g
```
rewrites the cache with what exists now. *happy*



CHIMO!
Bruce

---

### Post by Bruce M. on 2009-05-25
> **rocky5051 said:**
> EDIT: I seem to have posted just a moment too late (was typing, lol). His instructions are better.

And I was responding as you hit [Submit] - and Edit.  :)

But thanks regardless.
Bruce

---

