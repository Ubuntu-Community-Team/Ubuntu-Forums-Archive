---
title: "Contents of Partitions"
date: 2009-05-04
forum: General Help
---

### Post by Sonthun on 2009-05-04
Is there a way to just look at the contents of a particular partition?  One of the things that I still like better about Windows is how each partition is it's own drive.  This makes it easy to track.  I have one particular partition that is mysteriously full, but I can't figure out which files are in it to see what is filling it up.

Thanks.

---

### Post by taurus on 2009-05-04
To access a partition, you need to view the mount point.  If you mount /dev/sdb1 to /media/sdb1, then you would run something like

```
sudo du -h /media/sdb1
```

---

### Post by DGortze380 on 2009-05-04
> **Sonthun said:**
> Is there a way to just look at the contents of a particular partition?  One of the things that I still like better about Windows is how each partition is it's own drive.  This makes it easy to track.  I have one particular partition that is mysteriously full, but I can't figure out which files are in it to see what is filling it up.

Thanks.

Linux really essentially does the same thing.

As stated in the last post, partitions are accessible via their mount points. 

If you mount 

/dev/sda2 to /media/My Partition

the entire contense of sda2, directory structure in tact, will be available under /media/My Partition

Similarly, if you mount 

/dev/sdb1 to /media/My Extra Drive

the entire contense of sdb1, directory structure in tact, will be available under /media/My Partition

Devices generally do not share mount points just like two partitions aren't generally combined under one drive letter

---

### Post by pastalavista on 2009-05-04
The partitions (except /) should be listed in the Places menu just under the 'Computer'.. just click to open

---

### Post by Sonthun on 2009-05-04
Okay, this is probably my ignorance showing, but what about mount points that encompass other mount points.  For example, my boot partition is /, but /var/lib and /home are separate partitions.  When I run```
sudo du -h /
``` it shows me everything.

Just out of curiosity, why do you have to know the mount point?  Why can't you just search /dev/sdb1 instead of /media/sdb1?  Does the OS not know they are the same?

---

### Post by taurus on 2009-05-04
```
sudo du -h /home
sudo du -h /var/lib
```

---

### Post by DGortze380 on 2009-05-04
> **Sonthun said:**
> Okay, this is probably my ignorance showing, but what about mount points that encompass other mount points.  For example, my boot partition is /, but /var/lib and /home are separate partitions.  When I run```
sudo du -h /
``` it shows me everything.

Just out of curiosity, why do you have to know the mount point?  Why can't you just search /dev/sdb1 instead of /media/sdb1?  Does the OS not know they are the same?

If you haven't heard this one yet (although not entirely accurate, it's a decent way to think of things) Everything in Linux is a File.

/dev/sdb1 is a 'file' that contains a block device of a specific format, at a specific location on /dev/sdb

/media/sdb1 is a directory to which you mounted the contense of the /dev/sdb1 'file'

The reason it doesn't "know they're the same" is because they are not the same.

Windows handles things a little different, I don't know of a simple comparison, so you really just need wrap your head around the fact that the device and the mount point are two different thing.

---

### Post by Sonthun on 2009-05-04
Thanks for all the replies.  I appreciate it.  I just have one more question.  One of the things confusing me is that some of the directories under root are normal directories and some are partition mount points.  What command will only show me non-mount point directories under root?

Thanks again.

---

### Post by DGortze380 on 2009-05-04
> **Sonthun said:**
> Thanks for all the replies.  I appreciate it.  I just have one more question.  One of the things confusing me is that some of the directories under root are normal directories and some are partition mount points.  What command will only show me non-mount point directories under root?

Thanks again.

I don't know of one.

When you mount a file system, it is placed in the overall directory tree at the mount point. Thus everything is under /

That's just the way the tree structure is.

If everything is mounted in logical locations, I don't see why you would need to exclude them. (with the exception of some backup commands, etc.

What specifically are you trying to do?

---

### Post by Sonthun on 2009-05-04
Well, I partitioned my hard drive with 13 GB for root (sda1, ext3), 327 GB for var/lib (sda3, xfs), and 121 GB for /home (sda4, xfs).  A swap partition is sda2.  All 13 GB of my root drive are full and I can't figure out why.  I guess mostly I'm just curious about how this really works.  I don't like using things I don't have a good understanding of.  Plus, I'm going to do a re-install with a ssd and I'm trying to figure out if I just want to leave the whole ssd as root and then have another hard drive for /var/lib for my media files.

---

### Post by taurus on 2009-05-04
Maybe you want to check out the trash bin of root!  Maxing out 13GB when you have a separate /home & /var/lib is rare unless you have a backup daemon running that files up /var/backups.

```
sudo du -h /root
sudo du -h /var/backups
```
Also, it doesn't hurt to empty your cache.

```
sudo apt-get clean
df -h
```

---

### Post by pastalavista on 2009-05-04
> Well, I partitioned my hard drive with 13 GB for root (sda1, ext3), 327 GB for var/lib (sda3, xfs), and 121 GB for /home (sda4, xfs)

Why so much room for /var/lib?

---

### Post by DGortze380 on 2009-05-04
I would also check the size of your log files (depending on what you're doing on the machine)

/var/log

---

### Post by Sonthun on 2009-05-04
> Why so much room for /var/lib?

I'm running mythtv as well, so it is for recording.

I started going though each directory by hand and found that the /proc directory is listed as taking up 9 GB.  I thought it didn't have real files.  Just temporary settings files.  I suppose it doesn't really matter if that is the culprit since I'm going to reinstall.

Thanks for the help.  You've helped me better understand the linux file system.  I really switched over to Ubuntu and Myth just learn about new stuff.

---

