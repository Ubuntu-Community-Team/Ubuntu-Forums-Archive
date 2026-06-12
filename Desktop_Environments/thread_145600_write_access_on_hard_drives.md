---
title: "write access on hard drives"
date: 2006-03-16
forum: Desktop Environments
---

### Post by EastKY_DO on 2006-03-16
Can someone explain to me, in simple terms, how to change whatever settings need changing, to allow writing to hard drive partitions outside of 'home'?

I have fiddled with fstab, perhaps incorrectly, and am no closer to being able to use a spare partition with Ubuntu than when I started.  This is really frustrating.

Doc

---

### Post by Ramses de Norre on 2006-03-16
What's your fstab like now?
What filesystem are those partitions?

---

### Post by aysiu on 2006-03-16
If your other partition is mounted at /boot or /usr or just plain /, then you're not *supposed* to have write access to that without using *sudo*.

For more on modifying folders outside of /home, take a look at
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

If it's a Windows partition (FAT32 or NTFS), look at
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If it's an Ext3 partition, post the output of these commands ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by EastKY_DO on 2006-03-16
here's my current fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    auto,user,rw       0       0
/dev/hda3       /media/hda3     ext3    auto,user,rw       0       2
/dev/hdd1       /media/hdd1     vfat    auto,user,rw       0       0
/dev/hdd3       /media/hdd3     ext2    auto,user,rw       0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

the partition at /dev/hdd1 is a FAT32 formatted drive used for general storage.

---

### Post by Ramses de Norre on 2006-03-16
Change the line for it to something similar to this one: ```
/dev/hda1       /mnt/windowsk  vfat iocharset=utf8,umask=000 0 0

```

---

### Post by aysiu on 2006-03-16
Just so you know "similar to" means this: ```
/dev/hdd1 /media/hdd1 vfat iocharset=utf8,umask=000 0 0
```

After you do that, reboot your computer, and everything should be fine.

---

### Post by Ramses de Norre on 2006-03-16
I could have been more clear indeed:)
And instead of rebooting can't you just unmount the partition and then do sudo mount -a

---

### Post by EastKY_DO on 2006-03-16
Okay, I changed fstab per your advice and everything is cool.

Thanks mucho!

Doc

---

### Post by aysiu on 2006-03-16
[QUOTE=Ramses de Norre]I could have been more clear indeed:)
And instead of rebooting can't you just unmount the partition and then do sudo mount -a[/QUOTE] Yes, but then you have to walk people through the steps of unmounting and doing the *sudo mount -a*. Sometimes people claim "it doesn't work," probably because they did something wrong, and I don't feel like troubleshooting all that.

Rebooting is not a cardinal sin, and it's guaranteed to remount the /etc/fstab

---

