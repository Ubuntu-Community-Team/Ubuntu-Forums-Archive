---
title: "gnome crashed, I can't login"
date: 2006-12-30
forum: Desktop Environments
---

### Post by bincesu on 2006-12-30
i'm using edgy. a few days ago, i shut down my computer, and when i turned it on again, i couldn't start the session. i mean, i couldn't login. i enter my username and password, then i got continous messages on a blank orange screen : " unable to start session ", " gnome panel didn't start ", and so on... i can't remember now which applications can't start :).
i can't start terminal, either.
I don't recall any particular reason which may cause this.
Do i have to re-install gnome? I don't want to, neither re-install ubuntu...

Is there anyway to repair it? I'm not an experienced user.

Appreciate help, thanks....

---

### Post by taurus on 2006-12-30
Boot into recovery mode from GRUB menu and check to make sure you are not running out of disk space first!!!

```
fdisk -l
```

---

### Post by bincesu on 2006-12-30
Thank you. I've installed ubuntu on hda2 (4 GB) and it seems i've no free disk space. My hda4 is 20 GB, it's completely empty now, I guess i have to merge two partitions, right?
I'm running on LiveCd (dapper) and googling it now.
I must merge hda4 into hda2, without touching the data in hda2 (because it contains my system.)
Hda1 - Winblows (10 gig)
Hda2 - Ubuntu (4 gig)
Hda3 - Swap (1 gig)
Hda4 - free space, unallocated now (20 gig)

Any advice or hint?

---

### Post by taurus on 2006-12-30
What is the format of /dev/hda4?  Technically, you can move /home to /dev/hda4 and that would free up some space on /dev/hda2...

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
(Scroll down until you get to the section **[COLOR="Red"]Using the new partition[/COLOR]**.)

---

### Post by bincesu on 2006-12-31
hda4 was fat32, but i erased it using windows. Now it's unallocated.
But unfortunately moving /home wouldn't be enough, i think. Because my home folder is just 16 mb. 
The real problem is /usr/lib, it's 1.8 GB

I'm thinking to do this : (with a LiveCD)

*erase swap (hda3) -because it's between hda2 and hda4
*then resize hda2 -make it larger-, hope the data stay untouched :)
*finally create a new swap partition.

Before : hda2 -ubuntu- 4 GB + hda3 -swap- 1 GB + hda4 -empty- 20 GB
After    : hda2 -ubuntu- 24 GB + hda3 -swap 1 GB

Would it work?
I'm not sure, but i'll take my chances :)
Thanks for help, again...

---

### Post by bincesu on 2006-12-31
:-D

It worked great.

My partition table is like this now : 
hda1 :   10 GB - winblows
hda2 :   24 GB - ubuntu
hda3 :     1 GB - swap
hdb1 : 200 GB - fat32 (movies&music)

Thanks for all help....

---

### Post by bincesu on 2006-12-31
I've faced some problems.
Here is what i did :

1. boot with LiveCD

2. deactivate swap parititon

> sudo swapoff -a

3. open gparted, delete swap and hda4, resize hda2, create a new swap partition

4. reboot (at this point, ubuntu can't mount the new swap partition, because its uuid has changed)

5. get your new swap partition's UUID

> ls /dev/disk/by-uuid -lh

6. edit fstab, delete the old partition's data, and change your new swap partitions UUID 

> gksudo gedit /etc/fstab

7. reboot, it's done.

---

