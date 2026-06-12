---
title: "fsck died with exit status 8"
date: 2009-02-08
forum: General Help
---

### Post by ghstridr on 2009-02-08
I've seen a few of these posts here, but none seem to pertain to my problem.
During boot, init or some other process tries to write to either /var/run/pppconfig or /var/run/network/initialized and says it can't because the file system is mounted readonly.
Here is what the contents of /var/log/fsck/checkfs and checkroot:
```

Log of fsck -C -R -A -a
Sun Feb  8 17:24:07 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda6 is mounted.  e2fsck: Cannot continue, aborting.


/dev/sda7 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Sun Feb  8 17:24:07 2009
----------------
root@mgracy-laptop:/var/log/fsck# cat checkroot
Log of fsck -C -a -t ext3 /dev/sda1
Sun Feb  8 17:23:12 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda1: clean, 323423/4489216 files, 2061772/8960245 blocks

Sun Feb  8 17:23:12 2009
----------------

```
As you can see, / is clean.  I've booted to live cd's and forced checks and rescans for bad blocks and everything is coming up clean.
I can't figure out what is going on.  This happened after a power loss.
Now I'm at a loss.  Is there something that fsck might look for in the / filesystem to indicate a clean partition?
All this business of course leaves me at the 'Starting a maintenance shell.....Crtl+D to start up normally.....' So I do the Crtl+D and it starts normally and shuts down normally. :(

---

### Post by plucky on 2009-02-09
From a terminal post output of ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
``` -l is lowercase L not a 1

---

### Post by ghstridr on 2009-02-10
Actually I finally fixed it with e2dsck -pf on the /var and /home partitions.  Problem solved.

Thanks though!!!!

---

