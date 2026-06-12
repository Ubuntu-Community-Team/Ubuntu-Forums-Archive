---
title: "Repartitioning issues... HD is screwy."
date: 2009-01-19
forum: General Help
---

### Post by NCSmokeEater on 2009-01-19
Ok, I've got a Compaq Presario F700 with a 160GB (SATA) hard drive. 

During re-installation of Ubuntu (made some stupid decisions when I tried to install BT2), I chose the 2nd option for formating the drive. I think it was "Use Guided", but I could edit the parameters. I dragged the yellow Ubuntu 8.10 box to match the box above it (the before image). Apparently, I had it backwords. 

My hard drive/current install of Intrepid is seeing only 7GB to use (I have 122kB free now! Yes... KILObytes.). It's running on SDA6. I used the LiveCD and opened up the partition editor. SDA1 had 150+GB free, so I chose to shrink the size and turn the 150GB into unallocated space.

My question is, how do "hand over" the unallocated space to SDA6 for it to use? I don't want to have to reinstall everything again. I'm having enough issues between this and having to "Make Unload/Make Load" my Atheros drivers after every reboot.

If someone could walk me through how to get the free space over to my used partition it would be really great. 

Thanks so much for any replies!


EDIT:

After running "fdisk -l", here are the results.

```
# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007bac7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1062     8530483+  83  Linux
/dev/sda2           18115       19457    10787647+   5  Extended
/dev/sda5           19106       19457     2827408+  82  Linux swap / Solaris
/dev/sda6           18115       19056     7566552   83  Linux
/dev/sda7           19057       19105      393561   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by louieb on 2009-01-19
Not enough info to do anything but guess. Could you post a Gparted screen-shot?  or post your partition table by posting the output of
```
sudo fdisk -l
``` lowercase L at the end. 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by louieb on 2009-01-19
Looks like 1st you'll have to grow extended partition sda2 to the left to take up all the unallocated space.
Then you should be able to grow sda6 to left to fill the unallocated space so that it becomes a part of sda6.

---

