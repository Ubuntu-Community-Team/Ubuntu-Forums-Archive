---
title: "Transfering existing Ubuntu OS to a New Harddrive"
date: 2009-01-31
forum: General Help
---

### Post by frbe0101 on 2009-01-31
I got a new faster larger harddrive for my Dell Inspiron Laptop and I want to copy my existing k/ubuntu account to it. I plug the drives into my WinXP desktop and using partition magic 8 copied all the partitions (except the dell utility partition, which I can't seem to copy) I booted up the new drive on my laptop and get "Error 17" I tried changing what I could in the very limit bios but to no avail. I have been able to get a freshly installed ubuntu OS (64bit 8.10) but it will take me months to get everything working on it like I did in the old installer and I would rather like to duel boot the old (32bit 8.04) for now.

---

### Post by meindian523 on 2009-01-31
The best option would be to dd [or] rsync your installation to your new drive.I have experience with dd,rsync,not.I did ```
sudo dd if=/dev/sda of=/dev/sdb bs=512
``` where sda was the drive I had the install on(the source) and sdb the destination drive.I successfully replicated an 80 GB HDD,though it took quite a bit of time,around 2.5 hours approx.

---

### Post by frbe0101 on 2009-01-31
1. The laptop has only 1 sata port, only have access to one drive and that is the old one which boots. 
2. Copied OS does not boot on new drive, no terminal no nothing.
3. Only computer I have with the extra sata ports runs winXP only, assume my problem has to be solve within the winxp environment.

---

### Post by Slim Odds on 2009-01-31
> **meindian523 said:**
> The best option would be to dd [or] rsync your installation to your new drive.I have experience with dd,rsync,not.I did ```
sudo dd if=/dev/sda of=/dev/sdb bs=512
``` where sda was the drive I had the install on(the source) and sdb the destination drive.I successfully replicated an 80 GB HDD,though it took quite a bit of time,around 2.5 hours approx.

It's no wonder it takes so long. Why do specify the block size as 512? It's the default.

That means that each read and write is **VERY **small. That makes for lots of thrashing.

I'd specify a **much** larger size. Maybe 64K.

---

### Post by Slim Odds on 2009-01-31
BTW, it's not really as simple as this.

Using dd to copy the entire drive also copies the partition table and master boot record. Which is not what you want. If the drives were identical it might be OK. But the are different sizes which mean that the partition table must be different.

Also, when you change drives, you'll have to manually update your /etc/fstab to use the **new** drive ID's.

You really want to copy the data from individual partitions.

---

### Post by kevin11951 on 2009-01-31
I have fallen in love with [Clonezilla]("http://clonezilla.org/") over the past few months.

It is basically a clone of norton ghost, and copies partitions over to an image, such as to a dvd, cd, ext hdd, or other medium. the image is as big as the amount of data on the partition.

but it will copy to multiple cds/dvds if chosen.

---

### Post by Slim Odds on 2009-01-31
> **kevin11951 said:**
> I have fallen in love with [Clonezilla]("http://clonezilla.org/") over the past few months.

I second that!   I even use Clonezilla to backup my Windows laptop.

---

### Post by frbe0101 on 2009-01-31
Well I tried clonezilla before reading the replies and I have to agree: its &*^%ing awesome! I put clonzilla on a USB pocket drive, booted it, did a drive to drive image with it and it worked! 

so in short clonezilla is the way to go, once again a linux app (or in this case fully bootable linux base drive imaging dedicated OS) has shamed windows apps. #$%^ partition magic, thank god I got that for free.

Now for the next question: I'm going to install ubuntu 8.10 64bit on the unpartitioned side of the drive, **how do I go about insuring duel boot ability?**

---

### Post by grndslm on 2009-01-31
Depending on the size of your entire OS (/home folder included, obviously)... you might be able to use remastersys.

I've been able to use 8.10 with upgraded packages and nearly 500 additional packages, along with quite a few desktop backgrounds, themes, icons, etc. (excluding my /home directory) to create a 1.8 GB distro that I can hand out to anybody and there's not much more to it than creating a new user/pass & partitioning scheme.

There's also a backup mode with remastersys that would compress your /home folder too.  So if you used my distro.. you could definitely get more than 3GB of personal data in there too.  Compressed, you could prolly get a little more than 4GB, and if you don't add all the packages & themes on that I did.... that's even more data.

EDIT:  Also, make sure that you add the ntfsprogs package before you make your remastersys distro or backup... then you can resize a windows partition without the need for gparted livecd or similar solutions.  It'll all be on one disc.  So sweet and simple!

---

### Post by frbe0101 on 2009-01-31
Question: Can 2 different ubuntu OS share the same swap partition? Well I'm about the find out!  

> **grndslm said:**
> Depending on the size of your entire OS (/home folder included, obviously)... you might be able to use remastersys.

I've been able to use 8.10 with upgraded packages and nearly 500 additional packages, along with quite a few desktop backgrounds, themes, icons, etc. (excluding my /home directory) to create a 1.8 GB distro that I can hand out to anybody and there's not much more to it than creating a new user/pass & partitioning scheme.

There's also a backup mode with remastersys that would compress your /home folder too.  So if you used my distro.. you could definitely get more than 3GB of personal data in there too.  Compressed, you could prolly get a little more than 4GB, and if you don't add all the packages & themes on that I did.... that's even more data.

EDIT:  Also, make sure that you add the ntfsprogs package before you make your remastersys distro or backup... then you can resize a windows partition without the need for gparted livecd or similar solutions.  It'll all be on one disc.  So sweet and simple!

Nice, but I have ~70GB left on the unpartitioned side, so I got room.

---

### Post by frbe0101 on 2009-01-31
Failed, I can't see or boot the old 32 partition on ubuntu, even so Clonezilla clearly shows that the old partitions are still there and intact. 
[B]
How do I make the old Ubuntu 8.04 32 bit show up in the boot menu?[/B]

---

### Post by frbe0101 on 2009-02-01
Ok well I figured it out on my own. Its weird but 8.10 64bit sees 2 OS_part, one of which consist only of the 8.04 32bit boot folder contents. I simply copied parts of the old 8.04 GRUB menu into the new 8.10 menu. BAM, boot up 8.04 perfectly and the 8.04 does not see this divided OS_part anomaly (it sees it as unified), nor does it see the new 8.10 64 bit partition (it sees it as 80GB of unpartitioned space). Anyways, what ever, they both boot, and at least the 64bit can see the 32bits document/picture/video files.

so thread over

---

### Post by meindian523 on 2009-02-02
Please mark the thread solved.

---

