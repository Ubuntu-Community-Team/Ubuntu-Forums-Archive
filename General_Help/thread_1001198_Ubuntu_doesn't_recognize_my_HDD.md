---
title: "Ubuntu doesn't recognize my HDD"
date: 2008-12-03
forum: General Help
---

### Post by Miilou Suede on 2008-12-03
Hey there friends, I'm brand new to Linux! So I've installed 8.10 multiple times and still have not been able to successfully start it up once its finished installing.  Here's my mobo/hdd

Asus M2N-SLI nForce 560 Socket AM2 Motherboard
Not perfectly sure on my HDD. I believe it's a Seagate ATA 200 GB.  Any possible way I could use the Live CD to detect my HDD name/brand?

So I've got it all set up but each time when it comes to boot from my HDD it keeps on giving me the message "Gave up waiting for the root device! Dropping to a shell!" And then I'm down to BusyBox.  Any possible ideas of what I could do to actually run Ubuntu? (In layman's terms please. ;) )

---

### Post by taurus on 2008-12-03
So you still have Ubuntu on your harddrive right now?  Boot with the LiveCD.  Then, open a terminal and mount your harddrive.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
Assuming root partition, /, is on /dev/sda1.

Then, post the output of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /media/ubuntu/etc/fstab
```

---

### Post by Miilou Suede on 2008-12-03
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d0c8d0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23566   189293863+  83  Linux
/dev/sda2           23567       24321     6064537+   5  Extended
/dev/sda5           23567       24321     6064506   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="e9791bce-d755-42b0-afeb-cce6334b91f9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="35d5c4c3-ce77-416b-9728-27cddc78e40b" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ cat /media/ubuntu/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9791bce-d755-42b0-afeb-cce6334b91f9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=35d5c4c3-ce77-416b-9728-27cddc78e40b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Miilou Suede on 2008-12-03
Bumping this thread so it doesn't fall into oblivion. Is that bad conduct here?

---

