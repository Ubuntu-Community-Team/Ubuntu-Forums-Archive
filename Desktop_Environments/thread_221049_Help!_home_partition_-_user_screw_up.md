---
title: "Help! /home partition - user screw up"
date: 2006-07-22
forum: Desktop Environments
---

### Post by beameup on 2006-07-22
Nevermind. I reformatted, repartitioned and re-installed. Now it's done right. Good thing I have copies of everything.



Used a LiveCd and Gparted to create a new partition. I had a 100MB EXT3 partition I was resizing to 40/60 and was going to use the 60GB for my home partition.
It resized the partition and as it went to create it, it had an error and it didn't create the partition. GParted shows it as an "unknown filesystem" and now it doesn't boot at all. I get a GRUB Error 17. 

It's also a dual-boot machine with XP on a 40GB partition.

So what can I do to get my set up back? Do I reinstall GRUB? Did I lose all my data?  :???: :(


OK, attached a screenshot.
hda2 was the original ext3, hda4 was created after after the error.

---

