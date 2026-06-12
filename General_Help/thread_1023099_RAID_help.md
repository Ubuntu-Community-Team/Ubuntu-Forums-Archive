---
title: "RAID help"
date: 2008-12-27
forum: General Help
---

### Post by Mersenne on 2008-12-27
Hey,
I have a dell dimension 9100 with a 160 GB hard drive already with ubuntu functioning as a fileserver/webserver.
I got two 1 TB WD drives which I want to stick in RAID 1 into the ubuntu box as a separate drive which I will eventually mount to a folder.
I HAVE ALREADY INSTALLED UBUNTU.
All the searches I did only resulted in during installation RAID setup. How do I get these two drives as a separate drive in RAID 1?
Also, will all of the data get erased when I RAID 1 it with fakeraid? (I don't have a RAID card) If it won't, then I'll stick all of teh data first on one of the drives and then wait for them to mirror.

Any response would be very highly appreciated.

Regards,
mersenne

---

### Post by jnw222 on 2008-12-27
there is software raid

i belive dmraid might help (or cheat with an alt. cd (just go to partitner))

using that, you have to options

1. completely format both drives
2. resize partitions to make equal RAID areas on both devices


i would reformat both devices


also, why RAID?

it can be a huge space waste unless you NEED redundancy

---

### Post by Mersenne on 2008-12-27
> **jnw222 said:**
> there is software raid

i belive dmraid might help (or cheat with an alt. cd (just go to partitner))

using that, you have to options

1. completely format both drives
2. resize partitions to make equal RAID areas on both devices


i would reformat both devices


also, why RAID?

it can be a huge space waste unless you NEED redundancy

I do need failsafe redundancy and 1:1 mirroring
Anyway, what's an alt. cd? How do I get these? I'm a noob at this kinda stuff

---

### Post by jnw222 on 2008-12-27
alternate installer cd (text-mode install)

i am not that good with raid either

---

### Post by Mersenne on 2008-12-27
Uh I don't want to reinstall? Can anyone who's done this before help?

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Uh I don't want to reinstall? Can anyone who's done this before help?

If you want software RAID, then you need afaik the alternate iso image or the server iso image, and you will need to reinstall.
Backup your settings and important data, and read this :

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

It can be a bit confusing when you install with software RAID for the first time in Ubuntu, but it's a matter of 
1) First defining your RAID partitions.
2) Then appoint the mountpoints for them.
during the partitioning part of the installation.

Make sure to turn off any RAID in your BIOS if you prefer to use software RAID!

---

### Post by Mersenne on 2008-12-27
Wait so I can't just have an extra partition now wthout reinstalling?

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Wait so I can't just have an extra partition now wthout reinstalling?

You installed using the desktop installation cdrom, right ?
Or perhaps you installed using the server cdrom ?
If the latter, then you should have create "RAID partitions" during the partitioning part of the installation.

Perhaps it's still possible to make it software RAID, but that depends on your current partition scheme and how big your disks are.
If you have loads of free space, then you can do with resizing, but this can make things more complicated.

What is your reason against making backups, reinstall, and then restore your backups ?

---

### Post by Mersenne on 2008-12-27
Uh I have 2 NEW disks. Its currently running on a DIFFERENT disk!! So why can't I just insert in 2 disks and make it run?
I DO NOT WANT THIS TO BE MY BOOT DRIVE!!!!! I want this as a secondary drive!

I don't want to backup+reinstall since I have like a bunch of stuff installed and configured which will take too long to replicate later.

Oh yeah I did use the Ubuntu server disc

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Uh I have 2 NEW disks. Its currently running on a DIFFERENT disk!! So why can't I just insert in 2 disks and make it run?
I DO NOT WANT THIS TO BE MY BOOT DRIVE!!!!! I want this as a secondary drive!

I don't want to backup+reinstall since I have like a bunch of stuff installed and configured which will take too long to replicate later.

Oh yeah I did use the Ubuntu server disc

You could install on the disk which is not in use, and configure that for software RAID1 during the install *without* adding the other disk which is already in use to the RAID-array.

After booting with the new installed disk, you can copy everything over, and after that you can add the second disk to the RAID-array.

Do some reading first :

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)
[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)
[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)
[http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/](http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/)

Good luck!

---

### Post by Mersenne on 2008-12-27
Hey yeah that's not that bad of an idea actually lol.

Its that that SQL will get messed up.

Is there really no other way?

---

### Post by albinootje on 2008-12-27
Can you clarify the situation please ?
1) You have two new disks total.
Or 
2) You have one old disk with the installation and two new disks where you want the software-RAID on ?

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Hey yeah that's not that bad of an idea actually lol.

Its that that SQL will get messed up.

Is there really no other way?

Manually replicating an installation can be done.
And cloning a mysql installation is also no problem.

Please do some reading of those mentioned webpages first.

---

### Post by Mersenne on 2008-12-27
I have 1 160 GB drive with Ubuntu server on it etc etc.

I got 2 new TB drives that I want to RAID 1 together but not have an OS on it. I just want it to be like another drive.

Eh I read teh stuff. I don't want to reinstall anything lol.

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> I have 1 160 GB drive with Ubuntu server on it etc etc.

I got 2 new TB drives that I want to RAID 1 together but not have an OS on it. I just want it to be like another drive.

Eh I read teh stuff. I don't want to reinstall anything lol.

Good! :)

Now you only need to prepare (on the command-line) those 2 new disks to have software-RAID1, and after that format them, and start using them.
You can find out how to do that from the webpages I mentioned earlier.

---

### Post by Mersenne on 2008-12-27
> **albinootje said:**
> Good! :)

Now you only need to prepare (on the command-line) those 2 new disks to have software-RAID1, and after that format them, and start using them.
You can find out how to do that from the webpages I mentioned earlier.

Wait so I don't need to do any kind of reinstallation of ubuntu here right?

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Wait so I don't need to do any kind of reinstallation of ubuntu here right?

Yes, correct.

I assumed in the beginning you only had 2 disks, and 1 already in use.

---

### Post by Mersenne on 2008-12-27
> **albinootje said:**
> Yes, correct.

I assumed in the beginning you only had 2 disks, and 1 already in use.

Few more questions

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch) is the link I want right? I'm running Ubuntu Hardy (8.04). It will cross apply right?

Also, why can't I use teh dell BIOS RAID? That's much easier (Used it before). How do I get the drivers and stuff working then, since the dell one is much easier?

---

### Post by albinootje on 2008-12-27
> **Mersenne said:**
> Few more questions

[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch) is the link I want right? I'm running Ubuntu Hardy (8.04). It will cross apply right?


Have you dealt with the command-line before in Linux ?
You should know how to distinguish the different drives, before you run into trouble.

Posting the output of :
```

sudo fdisk -l
lshw -class disk -class storage -sanitize

```
can help with that.

> 
Also, why can't I use teh dell BIOS RAID? That's much easier (Used it before). How do I get the drivers and stuff working then, since the dell one is much easier?

Maybe that's an option.
Can you tell which type of Dell computer it is ?

And post the output of :
```

lspci

```

---

### Post by Mersenne on 2008-12-28
Yeah but I don't know too much in the way of it...like I know apt-get install, aptitude install etc. (the basix)

I'll post that soon

Its a dell dimension 9100

---

