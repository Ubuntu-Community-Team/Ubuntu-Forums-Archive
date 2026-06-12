---
title: "Corrupt superblock"
date: 2009-04-26
forum: General Help
---

### Post by madsporkmurderer on 2009-04-26
A few days ago, I installed some updates to my 8.10 install. When it rebooted I got all sorts of disc errors; I booted with a live cd and after a bit of searching ran fsck -yfv until it stopped reporting problems. I then re-booted and used the update manager to upgrade to 9.04.

It reported that various things had failed and then rebooted to the same sort of errors. I've booted from a live disc again and run fsck quite a lot of times (20 maybe, haven't been counting) and am still getting errors. I've just run fsck -p and got:```
ubuntu@ubuntu:~$ sudo fsck -p /dev/sda
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda
/dev/sda: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

It reports problems with an ext2 filesystem, I'm sure I formatted to ext3:confused:

The funny thing is that regardless of all these errors it seems to mount, read and write fine in this live environment.

Any ideas of what's wrong and how to fix it? Is is likely to be corrrupt partition tables/other system data or hardware failure? The drive is only about a year old.

Thanks a lot,
Mike

---

### Post by Pilen on 2009-04-26
Hi. I believe I have a similar problem as madspork.

I did a new installation with Xubuntu 9.04 AMD64 and after the installation I noticed that sda had lost the only partition on that harddrive, sda1. I haven't touched that drive in any way. It just disappered after the installation. Ubuntu is installed on sdb1.


```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2af62af5

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbffe294

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        3891    11719417+   5  Extended
/dev/sdb3            6445       14946    68292315   83  Linux
/dev/sdb5            3649        3891     1951866   82  Linux swap / Solaris
/dev/sdb6            2433        3648     9767457   83  Linux
```

If I use fsck it says: "Bad magic number in super-block while trying to open /dev/sda"

So how do I get back my partition? Please help me :)

---

### Post by madsporkmurderer on 2009-04-27
I wrote a script to run fsck -fyv /dev/sda1 50 times in a row, it's still reporting errors. While I've established that this isn't going to fix it, I'm pretty sure I've ruled out a hardware failure that is about to kill the disk.

It seems odd that the partition is obviously not that badly damaged because I can read/write to it, yet it reports all these errors. Is there a way to make it just boot from the drive ignoring these errors? Would this be a bad idea?

Thanks,
Mike

---

### Post by ibuclaw on 2009-04-27
Firstly, you run fsck on the partition, not the actual physical disk itself...

```
sudo fsck -p /dev/sda1
```

Secondly ... use e2fsck. ;)
```
e2fsck -fyv /dev/sda1
```

Just post any output from that.

Regards
Iain

---

### Post by ibuclaw on 2009-04-27
> **Pilen said:**
> Hi. I believe I have a similar problem as madspork.

I did a new installation with Xubuntu 9.04 AMD64 and after the installation I noticed that sda had lost the only partition on that harddrive, sda1. I haven't touched that drive in any way. It just disappered after the installation. Ubuntu is installed on sdb1.


```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2af62af5

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbffe294

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2432    19535008+  83  Linux
/dev/sdb2            2433        3891    11719417+   5  Extended
/dev/sdb3            6445       14946    68292315   83  Linux
/dev/sdb5            3649        3891     1951866   82  Linux swap / Solaris
/dev/sdb6            2433        3648     9767457   83  Linux
```

If I use fsck it says: "Bad magic number in super-block while trying to open /dev/sda"

So how do I get back my partition? Please help me :)

Looks like the hard drive is either not initialized, or you have deleted the partition off the hard disk.

Install gparted
```
sudo apt-get install gparted
```
Then go into **System->Administration->Partition Manager** and have a look at what it sees. My guess is that the whole drive will be "**unallocated**". I hope you didn't have any data of value on there :|

Regards
Iain

---

### Post by madsporkmurderer on 2009-04-29
It seems to have totally gone now, won't mount- just gives:
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg|tail
[  629.738927] end_request: I/O error, dev sda, sector 69
[  629.739650] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  629.739654] end_request: I/O error, dev sda, sector 65
[  629.739660] EXT4-fs: unable to read superblock
[  639.838536] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  639.838540] end_request: I/O error, dev sda, sector 65
[  639.838551] EXT3-fs: unable to read superblock
[  646.022972] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  646.022977] end_request: I/O error, dev sda, sector 65
[  646.022987] EXT4-fs: unable to read superblock
```

and fsck now gives:
```
ubuntu@ubuntu:~$ sudo  fsck -p /dev/sda1
fsck 1.41.4 (27-Jan-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

Also, when first booted from the live cd sda shows up in gparted, after I try to mount or fsck it is no longer shows up at all; if I reboot gparted finds it again.

What now?

Thanks a lot,
Mike

---

### Post by caljohnsmith on 2009-04-29
So you don't have any idea what might have happened that the sda1 partition somehow got deleted? Also, what file system was that partition? You could try recovering that partition with "testdisk"; first download the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sda drive and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions on that drive, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be the partition you want to recover.

John

---

### Post by madsporkmurderer on 2009-04-30
That doesn't find any partitions. There is a rapidly scrolling number for 'read error at', which I assume means that there are lots of read errors

Thanks,
Mike

---

### Post by madsporkmurderer on 2009-05-05
I've just been fiddling some more, gpart gives me:
```
ubuntu@ubuntu:~$ sudo gpart /dev/sda

*** Fatal error: cannot get sector size on dev(/dev/sda).
```

This looks bad. Is it reformat time? I assume I'd need a special formatting tool as it appears the partition table is gone as well. Or is it hardware failure?

Thanks,
Mike

---

### Post by madsporkmurderer on 2009-05-15
I've tried formatting and re-installing, but not even that will work- it exits with an I/O error when the partitioner attempts to re-partition the drive (I selected the 'use whole drive' option).

Is the drive totally dead? Can I somehow repair it?

Thanks,
Mike

---

### Post by thinman1189 on 2009-05-26
I'm having a similar problem. My thread can be found at [http://ubuntuforums.org/showthread.php?t=1170648](http://ubuntuforums.org/showthread.php?t=1170648)

What could be causing this? I've lost a lot if it can't be fixed.

---

