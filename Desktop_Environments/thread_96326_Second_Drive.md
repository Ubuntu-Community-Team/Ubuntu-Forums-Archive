---
title: "Second Drive"
date: 2005-11-28
forum: Desktop Environments
---

### Post by ohman11 on 2005-11-28
I have just put in a new 120 gig drive and ubuntu sees it as hdb....I am pretty new to linux and I dont know how to partition and format the drive. I have a win98 startup disk but when  I use fdisk it does not see the whole drive. Anyone know how to do this in linux?

---

### Post by Remmelas on 2005-11-28
It really depends on how you want to partition it, do you want to dedicate the whole thing to a single partition, split it up over different partitions, etc?  Perhaps of some help, could be gparted (gui partitioner), do ```
sudo apt-get install gparted
``` and it should show up on your applications->system tools menu i think.

---

### Post by ohman11 on 2005-11-28
[QUOTE=Remmelas]It really depends on how you want to partition it, do you want to dedicate the whole thing to a single partition, split it up over different partitions, etc?  Perhaps of some help, could be gparted (gui partitioner), do ```
sudo apt-get install gparted
``` and it should show up on your applications->system tools menu i think.[/QUOTE]

  I just want to use it as storage so maybe just 1 whole partition.

---

### Post by Brent Dax on 2005-11-28
[QUOTE=ohman11]I have just put in a new 120 gig drive and ubuntu sees it as hdb....I am pretty new to linux and I dont know how to partition and format the drive. I have a win98 startup disk but when  I use fdisk it does not see the whole drive. Anyone know how to do this in linux?[/QUOTE]
The tool you want is called "GParted" (for GNOME Partition Editor).  Under the System menu, go to Administration and choose Synaptic Package Manager.  Type in your password when prompted.  In the panel on the left, choose GNOME Desktop Environment, then find gparted in the list and install it.  Once it's installed, you can find it under Applications, System Tools, GParted.

Hope this helps.

---

### Post by ohman11 on 2005-11-28
[QUOTE=Brent Dax]The tool you want is called "GParted" (for GNOME Partition Editor).  Under the System menu, go to Administration and choose Synaptic Package Manager.  Type in your password when prompted.  In the panel on the left, choose GNOME Desktop Environment, then find gparted in the list and install it.  Once it's installed, you can find it under Applications, System Tools, GParted.

Hope this helps.[/QUOTE]
I did that..Thanks!  I created a extended partition for the whole drive now dont I need to format this?

---

### Post by Brent Dax on 2005-11-28
[QUOTE=ohman11]I did that..Thanks!  I created a extended partition for the whole drive now dont I need to format this?[/QUOTE]
It may already be formatted.  To see if it is, go to System, Administration, Disks.  Click on the new hard disk, go to the Partitions tab, and select the partition.  If it's not formatted, you can do so from here.  You can also use the "Access Path" function to control where the new drive will appear in your filesystem.  (Something like /media/Drive2 might be appropriate, unless you intend to move a whole area of the existing file system over.)

---

