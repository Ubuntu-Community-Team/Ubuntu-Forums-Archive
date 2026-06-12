---
title: "Merging Partitions on additional SATA drive(ntfs)"
date: 2009-03-11
forum: General Help
---

### Post by edy80y on 2009-03-11
Hi All,

I have been using Ubuntu 8.1 for a month now and loving it.  It is Currently installed on a 40Gb Hard Drive (happy to leave it there)

Prior to Ubuntu i had Vista installed on a 50Gb partition on a 400Gb Drive (ntfs formatted), with the remaining partition storing my media (music/movies etc).

What i want to do is to format the 50Gb to remove Vista and then merge it with the 350Gb to make it 400Gb as 1 drive , without losing (or risk losing) anything on the 350Gb partition. So I installed GParted, went to the 400Gb drive and right clicked on the 50Gb partition to format but the ntfs option was not available (greyed out). (screen shots of both disks in Gparted attached)

Is what i am asking possible to do?? Can this be done with a gui on the LiveCD perhaps??

Alternately, there is Acronis Disk Director which i have used in Windows which works a treat, maybe i can do this using an Acronis boot disk??

Cheers in advance,

Eddie

---

### Post by hikaricore on 2009-03-11
If the 350mb partition is your main Ubunut partition you will need to need to do this from a livecd.

First you will have to remove the 50gb partition.
Second you will need to move the 350gb partition to the front (this will take awhile).
Third you will need to resize the 350gb partition to fill the entire disc.

As with any partition editing there is ALWAYS risk of dataloss, but it is not common.
Please take care to backup anything you can not live without before doing anything of this nature.

---

### Post by edy80y on 2009-03-11
Thanks Hikaricore,

Ubuntu is installed on a seperate 40Gb HD (/dev/sda1)

The 50Gb and 350Gb in question is a separate drive (/dev/sdb1 and /dev/sdb2)

So, ill use your explanation anyways (after i backup the 350Gb partition), ill remove the 50Gb (/dev/sdb1) and slide it to the right, then resize to fit.

Cheers.

---

