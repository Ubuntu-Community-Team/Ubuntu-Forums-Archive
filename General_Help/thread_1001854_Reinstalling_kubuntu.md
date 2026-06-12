---
title: "Reinstalling kubuntu"
date: 2008-12-04
forum: General Help
---

### Post by Grigoros on 2008-12-04
Hi guys


  I have installed kubuntu 8.1 on my laptop and i have a 50-50 partition with windows. The problem is that i have to reinstall kubuntu due to some problems. When i start the instalation process and i come across to the partition task, i only see the two kubuntu partitions (i guess the old and the new) and i don't see at all the existing windows partition. How can i be sure that i will install kubuntu over the existing partition and over-write the windows partition?

 Thanx in advance ;)

---

### Post by eternalnewbee on 2008-12-04
Your windows are most probably in ntfs format. You should reinstall Kubuntu on your ext2 or ext3 partition.

---

### Post by Grolsche on 2008-12-04
ok lets just make sure your looking at the right bit in the partitions task.

When it first gets to the partition part, you should see 2 bars 1 over the other?

The top should show a 2 partitions one being ntfs (windows) and the other should be Linux (Ubuntu/Kubuntu etc)

The top bar should be what your drive partitions are now.

The bottom bar should show you the partitions after the manager has changed them.

If you select manual, then you should be able to select the partition you want it to overwrite?

Is this what your looking at or something else?

---

### Post by eternalnewbee on 2008-12-04
> If you select manual, then you should be able to select the partition you want it to overwrite?

Is this what your looking at or something else?
I'd say chances are 99% that's what Grigoros wants to do;)

---

### Post by Grigoros on 2008-12-04
I'm doing this on my laptop as i'm writing from another machine. :p
First i should say that i had the disk originaly 50-50. 120Gb for windows 120Gb for kubuntu.

What i see on the partition task at the moment is :  There are two bars horizontanly. They both say kubuntu 8.10 and each is 54GB (again 50-50) partition.

The options are:
Guided-resize SCSI1(0,0,0), partition #5 and use free space.

the other option is 

Guided- use the entire disk
SCSI1(0,0,0), (sda) 250GB  (which is the whole disk).

The third option is 
Manual


Now there is no place that the windows partition is mentioned. At least in the thing that i see.


So what should i do next???


Thanx a lot for your time. You are saving me

---

### Post by Grigoros on 2008-12-04
some more info on this

 I chose the manual option and  i see all the partitions now.

I deleted one of the linux partitions but it does not allow me to continue since it asks about a root partition. how should i treat this?

---

### Post by mc4man on 2008-12-04
edit
wrong method in this situation

---

### Post by Grigoros on 2008-12-04
i justed looked in the current settings and i have 

windows under      /dev/sda1
HP_recovery       /dev/sda2
current kubuntu  /dev/sda5

I guess i have to delete sda5???

then for the new partition i should choose one new mount point?

or example sda7?


This format does it formata the current partition and create a new one ?

---

### Post by mc4man on 2008-12-04
It will probably be easier if you do this in one step.
Go manual -> forward.
Double left click on your current kubuntu partition (sda5

That will open a 'edit partition' box.

In the 'use as' box choose Ext3 journaling system

Check the 'format partition box'

Set the 'mount point' to /

Click ok and proceed


Or run from kubuntu and post 

sudo fdisk -lu

---

### Post by Grigoros on 2008-12-04
[QUOTE=mc4man;6308768]It will probably be easier if you do this in one step.
Go manual -> forward.
Double left click on your current kubuntu partition (sda5

That will open a 'edit partition' box.

In the 'use as' box choose Ext3 journaling system

Check the 'format partition box'

Set the 'mount point' to /

Click ok and proceed


This is a silly question but:where should i set the mount point to?

---

### Post by mc4man on 2008-12-04
When you d. click on sda5 an "edit partition" dialog box will open.

( or click on (highlight) sda5, then click the "Edit Partition" box, same thing.

Do the three things mentioned below
> In the 'use as' box choose Ext3 journaling system
Check the 'format partition box'
Set the 'mount point' to /


see screen 
Edit: don't change the 'new partition size' from whatever it's set at, ie. what you see in the screenshot is not what you'll have

---

