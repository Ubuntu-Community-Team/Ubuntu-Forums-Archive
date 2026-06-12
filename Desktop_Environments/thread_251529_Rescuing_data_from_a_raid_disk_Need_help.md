---
title: "Rescuing data from a raid disk? Need help"
date: 2006-09-05
forum: Desktop Environments
---

### Post by Goonie on 2006-09-05
Hi all.

I have a hard drive that was part of a mirrored raid setup and I need to access the data on it. Can I mount it in Ubuntu as a normal hard drive?

Thx guys.

Goonie

---

### Post by TwoWordz on 2006-09-05
Yes you can. 

First try fdisk -l to see the partition on the disk, then mount it where you want. 

TW

---

### Post by Goonie on 2006-09-05
Thx... will try that in the morning :D

regards 

Goonie

---

### Post by Goonie on 2006-09-06
Well that didn't work :(

the partition is /dev/hda2 and fdisk says it's a Linux raid autodetect but the gnome disk manager says it's ext3. I tried adding the following line to fstab

/dev/hda2    /media/newdisk     ext3    defaults     0     0

and then mount it but got the message

/dev/hda2 is already mounted or /media/newdisk busy

Any ideas?

regards
Goonie

---

### Post by lha on 2006-09-06
Run
```
cat /proc/mdstat
```
to see if any md devices are up. Hopefully you'll see something like
Personalities : [raid1]
md0 : active raid1 hda2[0]
      80883732 blocks [1/2] [U_]

If you do, try to mount md0 or whatever you see in mdstat. At least the livecd started md devices automatically. Good luck. :)

---

