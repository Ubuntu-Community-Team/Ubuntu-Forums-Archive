---
title: "Can't mount filesystem without partition"
date: 2009-05-02
forum: Desktop Environments
---

### Post by Aperculum on 2009-05-02
Hi,
I have a problem when inserting certain usb-sticks and using my Nokia N73 in mass storage mode, because they present themselves as storage device without partitions, instead filesystem is directly on device and Ubuntu won't mount it.

What I mean, usually device is seen as, e.g. */dev/sda* and partition on it is */dev/sda1* which is then mounted, but in my case the device is seen as */dev/sda* without */dev/sda1* partition. It works if I mount */dev/sda* manually, but that doesn't really fix the problem.

Anyone have had similar problems? Anyone know how to fix this?

Cheers, Lauri

---

### Post by sahabcse on 2009-05-02
Try

mount -t ntfs-3g /dev/sda test -o force

Create test directory

---

### Post by Aperculum on 2009-05-02
It's not ntfs filesystem, it's plain ol' fat32 but without partition, so it confuses ubuntu automounter

**edit:** it works if I do > mount -t vfat /dev/sda test but my problem is that automounter won't do that

---

### Post by sahabcse on 2009-05-02
For mounting NTFS and Fat32 parttion follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by zeex on 2009-05-02
> **Aperculum said:**
> Hi,
I have a problem when inserting certain usb-sticks and using my Nokia N73 in mass storage mode, because they present themselves as storage device without partitions, instead filesystem is directly on device and Ubuntu won't mount it.

What I mean, usually device is seen as, e.g. */dev/sda* and partition on it is */dev/sda1* which is then mounted, but in my case the device is seen as */dev/sda* without */dev/sda1* partition. It works if I mount */dev/sda* manually, but that doesn't really fix the problem.

Anyone have had similar problems? Anyone know how to fix this?

Cheers, Lauri

Hi, 

I use USB stick and my MP3 player (Transcend T-Sonic 820) on ubuntu. Ubuntu always auto mount both of my devices. I never had any problem. My friends Motorola phone also mount smoothly. I'm using Ubuntu 8.10 and earlier 8.04

---

### Post by Aperculum on 2009-05-02
> **zeex said:**
> Hi, 

I use USB stick and my MP3 player (Transcend T-Sonic 820) on ubuntu. Ubuntu always auto mount both of my devices. I never had any problem. My friends Motorola phone also mount smoothly. I'm using Ubuntu 8.10 and earlier 8.04

Yes, my usb-sticks mount fine too, but that's because those have a partition on the volume and the filesystem is on that partition. If you mount any of those devices and do
> $ df -h
it'll show you that mounted device is */dev/sdX1*, but my problem is that if filesystem is directly on volume, without partition in between, automounter won't mount it.

---

### Post by Yoil1000 on 2012-01-27
> **Aperculum said:**
> Hi,
I have a problem when inserting certain usb-sticks and using my Nokia N73 in mass storage mode, because they present themselves as storage device without partitions, instead filesystem is directly on device and Ubuntu won't mount it.

What I mean, usually device is seen as, e.g. */dev/sda* and partition on it is */dev/sda1* which is then mounted, but in my case the device is seen as */dev/sda* without */dev/sda1* partition. It works if I mount */dev/sda* manually, but that doesn't really fix the problem.

Anyone have had similar problems? Anyone know how to fix this?

Cheers, Lauri

I have the same problem, but I have 1 more question, how can I mount it on windows? also, It's not possible to copy the data to a different partition by using "gparted", because it says "uncollected space". I'll like very much to know if you got some solution.

You can send me a E-mail [email]8450845@gmail.com[/email]

---

