---
title: "Can't  finish install"
date: 2009-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sailthesea on 2009-02-04
Hi Guys
 I'm trying to install 8.04 as a dual boot system on a Dell Latitude C640 running Windows 2000. I've backed up and deleted pretty much everything and defragged and have plenty of room but I can't work out how to partition the drive during the install. I don't know what manual settings I should use or even if this is safe to do. I'm using a Live CD and am wondering if I'm just just using the wrong distro or smething Any help would be great
Cheers

---

### Post by adult swim on 2009-02-04
hi sailthesea,
have you already created the partition where you want to install ubuntu?  if you havent yet, youll need to do that before you start the install process as you cant manage partitions within the installer.

---

### Post by armandh on 2009-02-05
if the existing OS is vista you must use the vista partition editor. I have found none other that will edit the "bullet proof" vista partition. 

for all others I use Parted Magic live disk and leave the desired space for ubuntu un partitioned.

In setup I select the "guided, use largest un partitioned space" option. Ubuntu then creates all the needed partitions.

---

