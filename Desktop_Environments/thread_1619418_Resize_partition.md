---
title: "Resize partition"
date: 2010-11-11
forum: Desktop Environments
---

### Post by badnaam on 2010-11-11
I have a dual boot Ubuntu 10.04 and Vista laptop.

My Ubuntu partions /dev/sda4 extended, which contains a /dev/sda5 ext4 and a /dev/sda6 ntfs partition.

Vista is on /dev/sda2 ntfs. I would like to wipe vista out, turn off dual boot (if possible) and use the space taken by vista to extend my /dev/sda6 ntfs partition in ubuntu.

What's the best way of doing this safely?

---

### Post by coffee412 on 2010-11-11
> **badnaam said:**
> I have a dual boot Ubuntu 10.04 and Vista laptop.

My Ubuntu partions /dev/sda4 extended, which contains a /dev/sda5 ext4 and a /dev/sda6 ntfs partition.

Vista is on /dev/sda2 ntfs. I would like to wipe vista out, turn off dual boot (if possible) and use the space taken by vista to extend my /dev/sda6 ntfs partition in ubuntu.

What's the best way of doing this safely?

Seriously, I would backup your home directory and wipe out all partitions and start over. If this is a new install and you dont have much in your home directory then much more the better.

Otherwise, You can use tar to backup your home directory or if its just a few files and you have a mem stick then just copy it all to that. Then reinstall.

My .02 cents worth.

---

### Post by cmcx_linux on 2010-11-11
I suggest you install gparted and have a look at your hard drive. From what I understand your layout might be something like so:

sda1: boot 100mb :-?
sda2: vista ntfs
sda5: ubuntu ext4
sda6: ntfs extra stuff?
----------------------
You would like to merge sda2 with sda6 but you have sda5 in between.

To do so, you would have to move sda5 at the begining of sda2 , move sda6 at the new end of sda5 ( which keeps the extended flag) and grow sda6 to fill in the new space at the end of your hard drive. ( This is how gparted would do it).

You would have 2 problems:
1. Because sda5 is mounted as / , you can not move it around the hard drive ( you can not work on a block level on mounted partitions). In this case, you would have to boot a live cd, given that you have enough ram, install gparted & friends ( support for working with the partitions you have, e2tools and ntfsprogs) and reorder your offline hard drive. ( you can use sudo apt-get install from the termial on live cds to install in RAM extra SMALL stuff)
2. In the bad event that vista is dumb enough to mark any bad sectors ( logically BAD, not physically) on sda6, any partition program will refuse to move the partition, and it might fail half way. In this case you would have your linux partitions moved and your windows parition stuck in the original position, or no windows partition anymore. It happened to me more than once.

You can also just wipe vista out, and reuse the space as a new partition and mount it somewhere in your directory tree ( it's the safest way). From what I experienced, with too big partitions, the lookups for files tend to be slower because of a heavy partition table. It's also safer to have your data distributed among more partitions, not just a big chunk. ( if the master tables from one ntfs get corrupted by bad sectors, improper shutdowns, etc, the other partition might be safe)

You can also try to install other flavours of linux, such as backtrack, on your new space to play with and experiment, or even a hackintosh, just for the fun of it.  
Have a fun one :popcorn:

---

### Post by badnaam on 2010-11-11
So if I just wipe vista out i.e. format that parition, will it mess up the booting process or will I just now be simply botting into ubuntu?

---

### Post by cmcx_linux on 2010-11-11
> **badnaam said:**
> So if I just wipe vista out i.e. format that parition, will it mess up the booting process or will I just now be simply botting into ubuntu?

The boot loader sits in your master boot record and from there adds extra stuff from your boot partition . In linux, the stuff needed for grub ( once loaded in MBR) are found in /boot/grub .. which is under sda5.. so it will boot if you delete vista. I sugest running an sudo update-grub ( or grub-update, short on memory regarding the order) from your terminal after you delete vista, so the boot menu will be updated accordantly. 
:guitar:

---

### Post by otherethe on 2010-11-11
> **cmcx_linux said:**
> The boot loader sits in your master boot record and from there adds extra stuff from your boot partition . In linux, the stuff needed for grub ( once loaded in MBR) are found in /boot/grub .. which is under sda5.. so it will boot if you delete vista. I sugest running an sudo update-grub ( or grub-update, short on memory regarding the order) from your terminal after you delete vista, so the boot menu will be updated accordantly. 
:guitar:
You can also format your vista, make free space Use it as a back up and are just some were to hold files such as movies, music ext so on, Move games to there as well such as world of warcraft for simple if you play just helpful hints for you to save you some pain, and you can also edit the Grub 2 by hand to boot for you much faster it's in /boot/grub/grub.cfg this is not always safe due to the fail safes that Ubuntu has if you run into errors but if you do run into errors you can always nano edit the file later to boot slower so you can select from the fail safes, Just open that file look for the line that looks like   set timeout=10 Change the 10 to a 0 and boom you boot instant with no Grub even poping up

You can also Backspace all of your Vista stuff out of the grub file as well

---

### Post by gouxiong on 2010-11-12
I am only to be mine !

---

