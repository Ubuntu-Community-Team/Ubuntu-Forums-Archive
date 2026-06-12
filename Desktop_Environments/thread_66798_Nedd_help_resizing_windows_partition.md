---
title: "Nedd help resizing windows partition"
date: 2005-09-18
forum: Desktop Environments
---

### Post by John W on 2005-09-18
I Have Windows XP and Ubuntu 5.04 as a dual boot setup.  Windows is on the first 20gig and Ubuntu is on the next 100 gig.  I would basically like to have WinXP have 100gig and Ubuntu 20gig.  WinXP partition is NTFS.  I tried sysrescuecd(QTparted) and it wouldn't let me shrink the Ubuntu partition so I could not increase the WinXP partition.   Is there a way I can accomplish this through Ubuntu?
Thank you ahead of time for your help

---

### Post by duan on 2005-09-18
Hi John,

I know this is not the ubuntu way but I successfully resized my NTFS partition (twice) with knoppix live cd (release 3.8 ). Using QTParted from the standard KDE menus.

However knoppix is a bit on the bleeding edge and difficult to maintain so I use ubuntu, and would also be interested to learn a way around resizing partitions with ubuntu.

Duan

---

### Post by aysiu on 2005-09-18
Did you use QTParted from a live CD or the Ubuntu you have installed? A partition cannot be resized while it is mounted, and if you're using that partition--it's mounted, trust me.

Use a live CD like Knoppix to QTParted your Ubuntu partition.

---

### Post by duan on 2005-09-18
I just booted the ubuntu live cd, its the same version hoary hedgehog as my hd install. it had no gparted installed so I did:

opened root terminal from menus
edit /etc/apt/sources.list and remove the comments before the universe repositories

then had to 
apt-get update 
(it was less than 1 minite to update on a 2Mbps line, so it is not bad)

apt-get install gparted
this took longer

then from that same root terminal
gparted

this happily gives me the option to resize any one of my partitions (ntfs, ext3 which has ubuntu on it) because only swap seems to be mounted.

However I have 4 partitions already and after the last resize of ntfs have 9 gigs unalocated but I cannot grow the first linux partition bigger :-(, and I have no Idea how to make an extended partition from it...

also I don't know if making an extended partition from the unallocated 9gigs is wise because all my boot setups and everything points to /dev/hda2. (where does the extended partition fit in?)

the partitions are in this order:
ntfs
unallocated
ubuntu root 
ubuntu /home
swap

I think this will at least get you what you want, John? (being able to shrink ubuntu partition)

Does this count as doing it the ubuntu way?

:-)

duan

---

