---
title: "Trouble installing Ubuntu"
date: 2006-08-08
forum: Desktop Environments
---

### Post by prodigytechno on 2006-08-08
hi im having trouble installing ubuntu into my pc, my pc got partitioned by error, so ive decided to install ubuntu into it.
i get to step 3 where it asks to choose my keyboard thing right.
then it just stays there forever, it doesnt go into step 4:sad: 
everything is connected, i have enough RAM (256)
so what is wrong?

please help me since ive been waiting to install ubuntu\

thank you

---

### Post by loserboy on 2006-08-08
hmm....i never heard of that before, are you running off of livecd, if so did you to the check for cd errors option before you finished booting?

---

### Post by JerMe on 2006-08-08
Someone correct me if I make mistakes...

It's *possible* that you're running out of memory.  There are several cases where 256MB isn't enough for a Dapper installation.

What you can do is try to turn on the swap so that the installation can finish.  I'll give you a run-down, but you'll need to read up it more since you already have existing data on the drive (and I don't want to be responsible for you losing your stuff!)  As always, back up your data before taking any action.

Boot the Live CD like you've been doing.  There's a partitioner on the Live CD called gparted.  Use gparted on the LiveCD to create a partition (10Gb or so) for a "/" partition Ubuntu, and a create a swap partition (512MB or so).  If you have to resize your existing partitions to give space, do it.

Next, open the terminal and type **sudo fdisk -l**.  That'll give you an output of all the partitions that you have on your drive.  We're looking for the swap partition that you just created in gparted.

Mine looks like this:

```
jerme@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612        5222    20972857+  83  Linux
[color=red]/dev/hda3            5223        5283      489982+  82  Linux swap / Solaris[/color]
/dev/hda4            5284       36483   250613998   83  Linux

```

see that red line?  The end of the line says **Linux swap**.  At the beginning of the line says **/dev/hda3**.  Your swap will be on a different partion, but the /dev/XdXX is your partition.

Next, type **sudo swapon /dev/XdXX**, where /dev/XdXX is YOUR swap drive partition.  If I were doing this, I'd type **sudo swapon /dev/hda3**.

So with all that, you partitioned your hard drive for a "/" and a swap, and you enabled the swap drive.  Hopefully that'll solve the issue and you can finish the installation in its entirety.  If that's the case, remember that you already partitioned your hard drive for Ubuntu, and that you don't need to repartition when the installer asks for it.  Just point the installer to the "/" and swap drives that you made and you'll be fine.  Hope this helps.

---

