---
title: "Can I add to my Ubuntu Linux partition?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-08-09
I have a linux partition, it is about 13 GB.  The rest of my 80 GB hard drive is windows, and I don't want to reformat.  

I have a 20 GB hard drive, but it is pretty old.  It is IDE, and my current one is SATA.  I want to know if I can either:  

1. Copy all the files onto the new drive, and expand the partition.

or (more preferably)

2. Add the 20 GB to my ubuntu partition.

How would I do this?

I have installed Ubuntu, but I apt-get installed KDE so I consider it Kubuntu.  I have many applications installed, and I installed UT2004 (which is why the partition was filled up so quickly.).  

What would I need to do this, or is it possible?

---

### Post by autocrosser on 2005-08-10
Well--I don't know if this will work, but--

When I changed to Ubuntu, I had partitions on my drive that I wanted to keep--I installed onto /, then edited (externally) my /etc/fstab to include my other partitions ( /home, /opt, /tmp)--Then rebooted--

My "extra" partitions were seen without a problem-- I would suggest you install the extra drive & try to make it your /home, /tmp & whatever you need to expand your system--I think that if you format the drive, create the directories & then take your existing data/load into the directories and edit fstab correctly---you "should" create a virtual drive that is the total of your 13 +20 - format space. 

 [-X **NOTE**I have not tried this with 2 drives--I "think" that it might work---I run a Mac system with four internal drives--All seen with Ubuntu ;-) 

I include my fstab for you to look at---
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hda4       /home           ext3    defaults        1       2
/dev/hda5       /opt            ext3    defaults        1       2
/dev/hda3       /tmp            ext3    defaults        1       2
/dev/hda9       /mnt/osx        hfsplus defaults        0       0
/dev/hdb2       /mnt/osx3       hfsplus defaults        0       0
/dev/hdb3       /mnt/games      hfsplus defaults        0       0
/dev/hdb4       /mnt/storage    hfsplus defaults        0       0
/dev/hdc3       /mnt/itunes     hfsplus defaults        0       0
/dev/hdd2       /mnt/downloads  hfsplus defaults        0       0
/dev/hde        /media/cdrom0   auto    user,noauto     0       0
/dev/hdf        /media/cdrom1   auto    user,noauto     0       0
/dev/scd0       /media/cdrom2   auto    user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

---

### Post by arcanistherogue on 2005-08-10
Well, I have a Serial ATA hard drive, so my main drive is read as sda, the windows partition sda1 and ubuntu sda2.  it will still work if i hava hda partition?

---

### Post by autocrosser on 2005-08-10
I would think that it would work--a drive is a drive is a---you get my idea--looking at man fstab, I see---"The first field, (fs_spec),  describes  the  block  special  device  or  remote filesystem to be mounted." So, as I read it, this will not preclude spreading a virtual drive over several "real" drives---sounds like a quasi-raid to me---

What I would do is create a "new" fstab & rename the orginal something like fstab_old in case the whole thing blows up--you can still rescue disk yourself back to "normal"--And the way I'm thinking of allows a "backup" because you have copied all the important info to the 20G drive--If it goes bad--recopy back to your boot drive, reboot & check for damage---You would need to enable the root user account if you havn't yet (I set-up root almost as soon as I set a "new" distro up--I know that there are "security" risks, but I like to meddle in my system more than most :? )--makes it easier to affect "global" changes----

Remember--This is not for the faint-of-heart--you are changing your system in a VERY basic level--The safe way to get what you want is to buy another SATA drive (120G or more)--use the IDE as a "transfer" point, and move to a drive with more room. I used my 120G to install Ubuntu (learned my lesson about not giving Linux enough room)--40G is reserved just for Linux & I off-load my "storage" to another drive.....

---

