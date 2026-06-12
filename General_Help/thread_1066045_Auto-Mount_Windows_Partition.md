---
title: "Auto-Mount Windows Partition"
date: 2009-02-10
forum: General Help
---

### Post by uho on 2009-02-10
I'm trying to run the command to mount my windows partition in sessions, however this requires sudo auth.

How can I automatically mount my windows partition on startup?

---

### Post by DeMus on 2009-02-10
> **uho said:**
> I'm trying to run the command to mount my windows partition in sessions, however this requires sudo auth.

How can I automatically mount my windows partition on startup?

Add the drives to your fstab file, situated in /etc. I did it like this:

/dev/sda2 /media/Datadisk ntfs-3g defaults,locale=en_US.UTF-8 0 0

Find out which partition the windows disk is and then add the line to the fstab file. The next reboot will give you the disk automatically.

Good luck

---

### Post by Slim Odds on 2009-02-10
> **DeMus said:**
> Add the drives to your fstab file, situated in /etc. I did it like this:

/dev/sda2 /media/Datadisk ntfs-3g defaults,locale=en_US.UTF-8 0 0

Find out which partition the windows disk is and then add the line to the fstab file. The next reboot will give you the disk automatically.

Good luck

/media is used for dynamic mounts. It would be best to put it somewhere else.

---

### Post by DeMus on 2009-02-10
> **Slim Odds said:**
> /media is used for dynamic mounts. It would be best to put it somewhere else.

Okay, where is "somewhere else"? I found out this worked for me so I use it, but if there is a better place I like to know it.

Thanks.

---

### Post by Slim Odds on 2009-02-10
> **DeMus said:**
> Okay, where is "somewhere else"? I found out this worked for me so I use it, but if there is a better place I like to know it.

Thanks.

It will work. I can just be confusing because other drives (like USB Flash drive, etc) will be mounted there automatically. So if you mix these there is a chance of getting confused.

You can put things like this pretty much anywhere you want. Just create a spot for it and put it there.

---

### Post by DeMus on 2009-02-10
> **Slim Odds said:**
> It will work. I can just be confusing because other drives (like USB Flash drive, etc) will be mounted there automatically. So if you mix these there is a chance of getting confused.

You can put things like this pretty much anywhere you want. Just create a spot for it and put it there.


Then I suppose /mnt is better?
About the confusing you mentioned: I gave my disks names so I always know which disk is which.

But thanks for the info.

---

