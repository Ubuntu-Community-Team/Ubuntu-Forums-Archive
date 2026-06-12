---
title: "real-time directory mirroring"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jewishj on 2006-06-03
I have setup a fileserver which has 6 hard drives with ubuntu 6.06.  Each hard drive is being used to archive its own type of thing, so like one hard drive is for anime, one is for movies, and so on.  I have one of the hard drives reserved for backups.  What I want to do is have real-time mirroring (like software emulation of RAID 1) of certain directories to the backup hard drive.  

I've also looked at mirrordir and rsync and neither of them seems to do real-time (I could be wrong).

---

### Post by djgrandmarquis on 2006-06-04
Have you thought about running rsync as a cron job? You could probably set it up to automatically run rsync, say, every 10 minutes. It's not 'real-time' but I think it would work.

---

### Post by jewishj on 2006-06-06
That would be fine.. but i'm really quite new at this and while I'm sure it's not that hard to do, maybe you could point me in the right direction as to how to set up a cron job like the one you suggested?

Thanks :D

---

### Post by saepia on 2006-06-06
I don't really remember rsync syntax (see **man rsync** command), but AFAIK rsync is intended to be network synchronization tool. Within one computer you can do it by using simple cp (see **man cp** for options which would overwrite only new files). If you want to add task to cron, for every 10 min do (in console):

crontab -e

in that file add line

*/10 * * * * your_command_here

save it, and close. your_command_here should be something rsync/cp related


If you know how to program, you can use FAM or GAMIN interface to monitor file changes and do something then.

---

### Post by djgrandmarquis on 2006-06-06
Here's how I use rsync:
[http://ubuntuforums.org/showthread.php?t=187894](http://ubuntuforums.org/showthread.php?t=187894)
It has one big advantage over cp: it can also delete destination files if they have been deleted from the source directory.

I don't have much cron experience, but I found this tutorial helpful:
[http://www.tech-geeks.org/contrib/mdrone/cron-howto.html](http://www.tech-geeks.org/contrib/mdrone/cron-howto.html)

good luck.

---

### Post by Ivan Matveich on 2006-06-06
Use software raid over a set of partitions or loop devices. For example

```

sudo -s

dd if=/dev/zero of=one bs=32M count=1
dd if=/dev/zero of=two bs=32M count=1
dd if=/dev/zero of=three bs=32M count=1

losetup -f one
losetup -f two
losetup -f three

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/loop[0-2]
mke2fs -j /dev/md0
mkdir raid
mount /dev/md0 raid

```

---

