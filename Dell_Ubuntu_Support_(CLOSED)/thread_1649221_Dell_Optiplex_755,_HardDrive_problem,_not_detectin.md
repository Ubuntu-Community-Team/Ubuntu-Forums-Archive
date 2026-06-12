---
title: "Dell Optiplex 755, HardDrive problem, not detecting"
date: 2010-12-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Supernoobie on 2010-12-19
Hi all, I'm fairly new to Ubuntu/Linux. Here's the problem I'm encountering after I tried to install Ubuntu Desktop 10.10

I was installing from a CD, as I tried to install alongside Windows XP, (The setup detected 2 hard drives, the first one was 40 GB, with all my windows stuff on it, the other was a 160 GB one), I got the message "error informing kernel about changes made to .....", which would not disappear no matter what I clicked. So, choosing the seemingly only option, I force powered down the computer. As I powered it back on, Windows did not boot, instead I just got a black screen of nothing but a flashing _. I tried booting from the LiveCD again, which worked well enough, EXCEPT, the 40 GB hardrive full of my Windows stuff and files was not detected, and the 160 GB drive was detected only in the drives tool, but not accessible. I have no clue as to how to: 1. retrieve important files from my 40 GB drive. 2. Restore Windows XP professional

PLEASE HELP :frown:

I will try to provide any information I can

---

### Post by ugm6hr on 2010-12-20
Where did you try to install Ubuntu?
Did you resize any partitions?
From the LiveCD, post the output from:
```
sudo fdisk -l
```
This will list all the drives and formats.
The priority should be to backup your files before we try and fix anything.
Did you backup before experimenting with installation?

---

### Post by Supernoobie on 2010-12-20
> **ugm6hr said:**
> Where did you try to install Ubuntu?
Did you resize any partitions?
From the LiveCD, post the output from:
```
sudo fdisk -l
```This will list all the drives and formats.
The priority should be to backup your files before we try and fix anything.
Did you backup before experimenting with installation?

Here are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b114

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19082   153274368   83  Linux
/dev/sda2           19083       19453     2972673    5  Extended
/dev/sda5           19083       19453     2972672   82  Linux swap / Solaris

(The computer has 1 gig of onboard memory)

And no, I didn't make a backup cause I'm a bloody idiot
I tried installing on the 160 GB drive, instead of on the 40 GB one with my Windows partition
Did not resize any partitions

---

### Post by ugm6hr on 2010-12-20
Oh dear..... The 40GB device appears not to exist at all.
The 160GB HD has been partitioned for an Ubuntu installation. If there is nothing of use on that HD, then there is no point in doing anything with it - you could just start from scratch and re-install when you've recovered your data.

Next thing to check is whether the 40GB device is even detected by BIOS. On Dell's it is normally F12 or Delete to enter the BIOS, and there should be a page for HD drives. See if it is there.

If not - then I have absolutely no idea what to suggest. And even if it is, then it will require someone with more knowledge than me to restore your data.

---

### Post by Supernoobie on 2010-12-20
> **ugm6hr said:**
> Oh dear..... The 40GB device appears not to exist at all.
The 160GB HD has been partitioned for an Ubuntu installation. If there is nothing of use on that HD, then there is no point in doing anything with it - you could just start from scratch and re-install when you've recovered your data.

Next thing to check is whether the 40GB device is even detected by BIOS. On Dell's it is normally F12 or Delete to enter the BIOS, and there should be a page for HD drives. See if it is there.

If not - then I have absolutely no idea what to suggest. And even if it is, then it will require someone with more knowledge than me to restore your data.

It's possible that I was mistaken and the windows "drive" was a partition of the 160 gig drive... in that case do you think TestDisk or Photorec will work? I have not written in the hard drive yet.

---

### Post by ugm6hr on 2010-12-21
> **Supernoobie said:**
> It's possible that I was mistaken and the windows "drive" was a partition of the 160 gig drive... in that case do you think TestDisk or Photorec will work? I have not written in the hard drive yet.

If that's true, then... Maybe.
The 160GB drive has been repartitioned, with the new partitions over-writing the old Windows one.
I have no experience of TestDisk etc.
I would suggest reposting a new thread in the General Help section explaining exactly what you want - with a sensible title about file recovery.
Good luck.

---

