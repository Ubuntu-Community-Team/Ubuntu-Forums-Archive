---
title: "Problem mounting usb"
date: 2014-09-03
forum: Desktop Environments
---

### Post by dkostovasilis on 2014-09-03
Hello,

I am having a problem mounting my USB-stick device. I tried some of the most common solutions online but without success.
The data on the drive are very important and I need to keep them.

I think the problem originates from the fact that I messed the grub system file  (/etc/default/grub) and the computer would not boot.
So what I did was to boot in recovery mode > root commang window > "mount -o remount,rw /" > then edit grub to revert my changes.
(I may have forgotten the "/" in "mount -o remount,rw /")

So after I update grub, I boot ubuntu as normally and my device will now not mount. Its a 32 GB drive which was attached to the computer while the above process.
I did try to mount it manually with no success.

sudo fdisk -l returns

```
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7812925

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304803839   152400896   83  Linux

Disk /dev/sdb: 32.1 GB, 32128368640 bytes
64 heads, 32 sectors/track, 30640 cylinders, total 62750720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fcdd958

Disk /dev/sdb doesn't contain a valid partition table
```

Also sudo mount /dev/sdb /media -t ntfs gives

```

NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

ls -l /dev/sdb
```
brw-rw---- 1 root disk 8, 16 Sep  3 15:36 /dev/sdb
```

GParted has it as "/dev/sdb: unrecognised disk label"
Opening photorec doesn't even show the usb. Creating an image of the drive through disks gives 28 GB of unreadable data and a whole lot of nothing...

Running Ubuntu 14.04.1 freshly installed on a laptop.

Any help would be greatly appreciated. Again I emphasize that the data on it are very important to me.
Thanks
D.

---

### Post by yancek on 2014-09-03
Not knowing what some of "the most common solutions" you tried are we are left to guess?
Do you have any idea what change you might have made to /etc/default/grub, again we can only guess if you don't know.
If you forgot the '/' in the command you posted then I doubt anything was done or any changes were made as the / means the root filesystem.  I've never been unfortunate enough to have to use the command so I can't be certain.

> Also sudo mount /dev/sdb /media -t ntfs gives

The error reported from this command means that you did not try to mount a filesystem which needs to be on a partition such as sdb1.  Given the other information you posted, I doubt that changing sdb in the above command to sdb1 would help as your fdisk output shown no sdb1 partition and apparently gparted does not either?  Testdisk and photorec are the best possibilities for recovery.  Since the partition on that drive was apparently windows ntfs, have you tried recovering from a windows system?

---

### Post by dkostovasilis on 2014-09-03
Thanks for your reply yancek. Sorry for the vage information but I am/was kind of in a panic!
What I have tried is to find the device (listed only as /dev/sdb), try to mount it manually (as above) check drivers for ntfs-3g and try testdisk and photorec.

After fidling around photorec managed to bring some files back (about 1/10) but with non-representative names and no structure at all.
I really need some 2000 document files with their names and structure.

I have also tried mountind sdb1 but with no success as it can't be found.
Now working on a different machine (Ub. 14.04.1 again) and still not recognised.

The change in Grub was in the line **GRUB_CMDLINE_LINUX_DEFAULT **.
Since I am on a different machine I can't find what I tried to put in it but I will post it as soon as I get it.

---

### Post by yancek on 2014-09-03
Your fdisk output shows just the one Linux partition on sda1.  Was the flash formatted windows, ntfs?
I don't see how editing that line or anything else in that file would cause the problems you are reporting as those are boot parameters.

---

### Post by dkostovasilis on 2014-09-03
I don't suppose it would thats why I didn't include more info on this.
Initially I thought this would be an issue of root pemissions that I assigned without removing the USB.
But it starts to appear that the usb has gone bad. Let's see if someone has any idea...

---

### Post by BigJules on 2014-09-21
Why not take the USB stick to another 'buntu computer? 
This way if it works, you get to save your data and find out if it is FAT or NTFS. 
If it doesnt, you know its the device, not your computer.

---

