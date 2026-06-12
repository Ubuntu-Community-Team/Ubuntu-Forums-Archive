---
title: "Unable to Access / Format Extended Drive"
date: 2005-11-07
forum: Desktop Environments
---

### Post by tagg3rx on 2005-11-07
Hi All Need some help here - it appears 95% of my harddisk is unformatted and inaccessable.

I have a 10 gig HD
In system - admin - disks
it shows my hd partitioned into 2 drives (1 and 5)
/dev/hda1 looks fine but is only 243 MB
/dev/hda5 says its unformatted and inaccessible

I do a sudo cfdisk
and get 2 Harddrives listed hda1 and hda5
I select
hda5 (blank) Logical Linux LVM (blank) 997.27
Select write as it seems the closest to format

It says Wrote Partition table, but re-read table failed reboot to update table

So I rebooted

Loaded up system - admin - disks
Choose Hard disk > Partitions tab and have 2 partitions hda1 looks fine
hda5 indicates:
access path none (i have tried changing to home)
size 9.29 GiB (free space not avial)
Status Inaccessible

I have clicked format and a status bar jumps to 100% but nothing happens
I have clicked enable and it goes grey but comes back the same

So how do I format this drive (and make it the default place where I save data)

Thanks ubuntus
Tagg3rX

---

### Post by tagg3rx on 2005-11-07
*bump*
Help Please

---

### Post by psusi on 2005-11-07
It sounds like your disk is formatted for LVM.  I don't think the gui tools support LVM.  You might want to man lvm and see what you can do with the command line utilities.  

How did you originally partition the disk and install ubuntu?

My guess is that you installed ubuntu to the first partition, and the rest is configured for LVM.  I'd recomend repartitioning without LVM using gparted.  Either that or learn to use the command line LVM tools.

---

### Post by RAOF on 2005-11-07
[This post]("http://www.ubuntuforums.org/showpost.php?p=474373&postcount=3") has some links which may help.

---

