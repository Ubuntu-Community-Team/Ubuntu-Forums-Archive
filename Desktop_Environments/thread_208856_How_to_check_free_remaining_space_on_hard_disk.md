---
title: "How to check free remaining space on hard disk?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by orbital on 2006-07-04
How can I check the remaining free space on my hard disk the easy way in Kubuntu?

---

### Post by ozorba on 2006-07-04
From the command line type

df -a

This will give you more than the empty disk space...

OZ

---

### Post by orbital on 2006-07-04
Is there a reason why I can't check this without using the command line??

---

### Post by smoove on 2006-07-04
Yea, would be a good idea!

---

### Post by Flamekebab on 2006-07-04
I always just look at the status bar in Nautilus, it tells you how much free space remains. This gets complicated if you have multiple hard disks and partitions though.

---

### Post by orbital on 2006-07-04
Yeah I know it works with Nautilus, but how about Kubuntu and Konqueror? It doesn't show the free disk space at all I guess....

---

### Post by Jucato on 2006-07-04
I just learned this very recently from aysiu:

Right-click on an empty space in Konqueror (make sure you are browsing a folder), then click on Properties. The last two lines of the dialog box that pops out tells where that folder is mounted, and how much free space there is in that mount point/partition.

---

### Post by Thund3rstruck on 2006-07-04
Actually its much easier to use the 'h' switch since that makes it human readable (in MBs).

```

df -h

```

As far as not using the command line... err, this is linux...the command line is what makes linux great

---

### Post by orbital on 2006-07-04
[QUOTE=Thund3rstruck]
As far as not using the command line... err, this is linux...the command line is what makes linux great[/QUOTE]

Agree completely, and I use the df command all the time. But we are talking about a basic feature that every file manager should have (just like Nautilus has).

---

### Post by Jucato on 2006-07-04
@orbital: have you checked the method I gave?

---

### Post by Matthew Bartram on 2006-07-04
In gnome, the "system monitor" will tell you the space, used etc. of partitions. In KSysGuard (looks like the KDE equivalent), under the sensor browser, you can add displays for the partition information.

---

### Post by oobuntoo on 2006-07-04
To check remaining free space of partitions on Kubuntu:

kmenu->System->KinfoCenter and choose Partitions

or simply type "kinfocenter" on Konsole and choose Patitions.

---

