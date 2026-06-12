---
title: "GParted Need HELP!! :)"
date: 2009-04-01
forum: General Help
---

### Post by gschier on 2009-04-01
Hello fellow Linuxians.  I'm having a problem with my partitions.  I recently got rid of my windows xp partition and i would like to make my Ubuntu partition(ext3) use up the whole disk (or merge with the unused ones). as in the picture below, the sda7 and sda2 are both not in use right now so i want to use those to expand my ubuntu.  Any ideas?
THANKS):P





[img]http://i34.photobucket.com/albums/d139/krazycid10/Screenshot-2.png?t=1238627885[/img]

---

### Post by louieb on 2009-04-01
Welcome to Ubuntu forums.
Can't think of a simple way to merge your partitions together.  You won't be able to do it from your Ubuntu hard drive install. You will need to use a live CD. Since the Ubuntu live CD has an older version of Gparted, I use Gparted from the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") 

Just a suggestion.  Might try a fresh install.  When you get to the partition part of the Install. choose manual partitioning. Click on sda2 and choose a mount point of / (root) at 13GB  that is plenty of room.  Then click on sda7 and choose /home for its mount point. 

You'll still have access to anything in your current install. I fact the new install should give you the option of booting your current install or the new one. 

Then you still have sda5 as a testing ground. Good Luck.

---

### Post by gschier on 2009-04-01
but sda5 is my current install and i would like to keep using it but its full to the top with installed programs that i need.  Is there a way to clone an ubuntu installation with all currently installed programs and settings?
I know i could just reinstall everything but then i lose everything :mad:

---

### Post by SikEnCide on 2009-04-01
Delete sda7...

Now you should have some open spaceo n the drive.

Extend sda2 to fill the rest of the unpartioned space.

---

### Post by 3Miro on 2009-04-01
Before you do anything to the partitions MAKE SURE TO BACK UP ALL IMPORTANT DATA.

I think it is possible to delete a partition and then expand a neighboring partition in to the empty space, however, I have never done that. Try finding a manual or someone who knows how o do it. In any case, you can only "merge" neighboring partitions.

---

### Post by louieb on 2009-04-01
Hey I like SikEnCide's idea. Delete sda7, move your swap to the end. Then grow sda5 to fill the space.     

Yes you can clone sda5 to another partition. (lots of ways one is Gparted can do that)  Such as sda2 or sda7 But its not simple for someone thats new to Linux. 

The short of it use Gparted to copy sda5 to sda2 or sda7. 
fix grub to boot the new partition.
fix /etc/fstab to use the new UUID  
fix /boot/grub/ to use the new UUID.  

It just that to get Ubuntu to use the whole disk is going to require a major change to your current partition structure.   But if you want to try and need real time help. Install Xchat on the irc.freenode.net server and join one of these chanels #ubuntuforums-beginners, #ubuntuforums or  ##beginners-help . 

Here a couple of links about partitions and using Gparted.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 
and Grub [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") 

I only suggest doing a fresh install because thats the easiest way to go.
Gota go. back in few days to see how it went. Good luck.

---

