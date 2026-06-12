---
title: "home partition says its full but there's space."
date: 2009-01-20
forum: General Help
---

### Post by rmills on 2009-01-20
I was trying to copy a ubuntu cd image into my home directory when it said that there was only 634MB remaining and 699MB were needed.  I have a 120 GB hard drive in my laptop.  It's currently triple booting Windows XP, BackTrack3 and Ubuntu 8.04.  It's partitioned as follows:
partition #1 = 20GB ntfs (XP)
partition #2 = 11GB ext3 (Ubuntu)
partition #4 = 5GB ext3 (BT3)
partition #3 = 77GB ext3 (home/storage)

I use partition #3 as my home partition and it's mounted to /home in Ubuntu on boot by fstab:
```
/dev/sda3       /home   ext3    nodev,nosuid    0       2
```

When I checked the HD space you can see that there's a disconnect @ /dev/sda3:
```
rmills@700m:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             11300220   4090724   6639992  39% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  769100       100    769000   1% /var/run
varlock                 769100         0    769100   0% /var/lock
udev                    769100        48    769052   1% /dev
devshm                  769100         0    769100   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                     769100     39792    729308   6% /lib/modules/2.6.24-23-generic/volatile
/dev/sda3             79667972  75021400    631528 100% /home
securityfs                   0         0         0   -  /sys/kernel/security
/dev/sda1             20490872  19331500   1159372  95% /media/disk-1
```

79667972 - 75021400 = 4646572 not 631528!  Does anyone know what might be locking up my disk space and how to clean it out?  Thanks!

---

### Post by jrusso2 on 2009-01-20
I am not sure.  Maybe a lot of temp files?  Did you store some large videos or DVD's in your /home?

Anyways it looks full you will have to list all the directory sizes and see what you get that has a lot and take a peek inside.

I know when I decrypt a DVD it leaves a copy after I resize I have to remember to delete that.

---

### Post by jamesrl on 2009-01-20
It's possibly due to the fact that 5% of your hard drive is reserved for root by default with ext2/3 partitions:
[http://boncey.org/2006_11_18_reclaiming_ext3_disk_space](http://boncey.org/2006_11_18_reclaiming_ext3_disk_space)
or its an artifact of files you currently have open, which you should be able to check with lsof.
PS: Go Sox.

---

### Post by rmills on 2009-01-20
I have a few movies.  They were ripped from the DVD on another machine and only the .avi files are on this one. I've got a ton of photos and music (25GB and 35GB respectively).  On that partition the directory structure looks like:
```

/home
     /rmills
            /Desktop (1 item with 56 bytes)
            /Documents (nothing yet)
            /Music (14,009 items, totalling 35.5GB)
            /Pictures (7,872 items, totalling 25.6GB)
            /Videos (19 items, totalling 9.8GB)
            /<a whole bunch of hidden files> (4,729 items, totalling 304.1MB)

```

The listed sizes just don't add up.  There shouldn't be any tmp files stored on the partition as that's all on the root partition.

---

### Post by rmills on 2009-01-20
Ah! Thanks james.  Time to reboot.

---

### Post by rmills on 2009-01-20
```
tune2fs -m 1 /dev/external
```

Worked like a charm!  Wish there was someway to give you rep.  Thanks again james.

---

