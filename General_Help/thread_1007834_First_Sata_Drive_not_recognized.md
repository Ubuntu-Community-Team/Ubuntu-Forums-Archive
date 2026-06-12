---
title: "First Sata Drive not recognized"
date: 2008-12-10
forum: General Help
---

### Post by denster on 2008-12-10
Hi all,

I have an issue where my 1st Sata drive isn't being acknowledged or at least I cannot access it, it is not showing up in gparted or in terminal with fdisk -l

I have 5 Sata drives and they are listed in BIOS in the same order as connected to MB.

What puzzles me is that this problem occurs intermittently, as sometimes the drive shows up, like every other boot or so.

Ubuntu is on my 2nd hard drive in reality, but when the problem occurs, Ubuntu sees the 2nd drive as sda, of course. So 4 of the 5 drives show up fine, just the first one gets dropped somewhere into the abyss...

I boot to the first drive all the time and it is always seen by my other OS's, and the drive is fairly new and no indications of failure.

I do have a raid 0 on the last 2 drives and I have added rootdelay=90 to the kernel line in menu.lst, as I was getting dropped to busybox at boot.

Would appreciate any help -thank you

---

