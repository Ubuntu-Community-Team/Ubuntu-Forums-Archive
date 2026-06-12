---
title: "Slow transfer speed SATA HDD to SATA HDD."
date: 2009-01-17
forum: General Help
---

### Post by Roasted on 2009-01-17
I just formatted my system and I have a backup drive of the same size that I rsync my data to. I mounted the hard drive in /etc/fstab with the UUID and rebooted two or three times for other reasons (updates and whatnot).

Now I'm trying to transfer 160gb of data from my backup drive to the home directory of my primary drive, and at first I was pulling speeds of 40mb/s but now it's dipped down to 6mb/s... leaving the data to take 6 hours to transfer back.

With this same amount of data in the same situation in the past it's taken roughly 40 minutes to transfer everything. I have no idea what's different this time around that's causing the problem.

Both drives are 500gb SATA II 3.0gb/s drives with 32mb cache.

Any ideas?

---

### Post by Feivel on 2009-01-17
> **Roasted said:**
> I just formatted my system and I have a backup drive of the same size that I rsync my data to. I mounted the hard drive in /etc/fstab with the UUID and rebooted two or three times for other reasons (updates and whatnot).

Now I'm trying to transfer 160gb of data from my backup drive to the home directory of my primary drive, and at first I was pulling speeds of 40mb/s but now it's dipped down to 6mb/s... leaving the data to take 6 hours to transfer back.

With this same amount of data in the same situation in the past it's taken roughly 40 minutes to transfer everything. I have no idea what's different this time around that's causing the problem.

Both drives are 500gb SATA II 3.0gb/s drives with 32mb cache.

Any ideas?
I thought it was just me. I had slower transfer speeds not only between SATA drives but also between 2 partitions on the same SATA drive. Transferring files from either SATA drive to an external (USB 2) drive was just over double the speed.

---

### Post by Roasted on 2009-01-17
I don't know if it was something to do with how I mounted it in fstab or not, but I took the entries for my 2nd drive out of fstab and rebooted. Then I manually mounted it via terminal:

sudo mount /dev/sdb1 /media/localbackup

I'm transferring the data over. It started at 75mb/s, and eventually settled down to 40ish mb/s.

I don't know what I did wrong. On my last install I had fstab set up and it transferred real fast with no problems. 

Hmm???

---

### Post by dcstar on 2009-01-17
> **Roasted said:**
> 
........
With this same amount of data in the same situation in the past it's taken roughly 40 minutes to transfer everything. I have no idea what's different this time around that's causing the problem.

Both drives are 500gb SATA II 3.0gb/s drives with 32mb cache.

Any ideas?

I don't know for sure, but I have these options in my fstab EXT3 entries to stop the unnecessary writes every time a file is read or a directory is accessed, it may speed things up a bit:

```
nodiratime,noatime
```

---

### Post by Roasted on 2009-01-17
Hmm, weird. Maybe my spacing/tabs weren't in right... cause I manually set up my fstab this time. But just to get my data over, I just took out the entries in fstab and manually mounted it to move my stuff from my backup drive to my primary. After that, I remembered I had a copy of my fstab saved, so I pasted over the saved entries for fstab and rebooted. My drives mounted just fine. 

I tried to copy over a copy of my music directory from my backup drive to my main drive, just to test the speed of the drives on fstab, and I pulled decent speed as I was before when I manually mounted it.

So I'm not sure if I had a messed up entry in my fstab or not. But, the moral of the story is, the speed of the drives shouldn't matter whether it's mounted by UUID in fstab as opposed to manually mounting it via mount /dev/sdb1 /media/localbackup in terminal... am I right? Like the performance should be the same, right? It's just a matter of convenience to have fstab mount it automatically...

Is my train of thought accurate?

---

