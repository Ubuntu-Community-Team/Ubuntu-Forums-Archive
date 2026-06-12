---
title: "Really Messed Up Partitioning"
date: 2005-08-11
forum: Desktop Environments
---

### Post by drizek on 2005-08-11
This is the weirdest thing ive ever seen in linux. ive been trying to install gnome, but synaptic keeps telling me that i have no room left. i have my / on a 25GB partition. HTF can i not have any room left?

so i go in and start looking at the different folders in this part(hda4) and i find a directory called home. i click on it, and it takes me to my home partition, hda6. For some reason, home is taking up 23.5GB of space on both my / partion AND my /home partition. im afraid to delete the home folder in /, but its going to screw up my computer if i keep it like this. WTF?

---

### Post by blind0wl on 2005-08-12
hehe...yep, the default install sounds like its only allowed a small amount of room for you / and allocated everything else to /home.

Post the output of df -h here and this will confirm it.

---

### Post by autocrosser on 2005-08-12
That sounds kind'a like how I "saved" my user data from YellowDog when I installed Ubuntu---I installed Ubuntu on the / partition--then edited /etc/fstab to use /dev/hda3 as /tmp--/dev/hda4 as /home & /dev/hda5 as /opt (just how my system was set-up in YellowDog)--rebooted to a rescue disc & deleted the /home, /opt & /tmp directories from /---then booted into Ubuntu normally--had zero problems with doing it this way.

Check your /etc/fstab to see where your system "really" is--if you "really" have a seperate /home & it is as complete as the one you see in Nautilus--nuke the one in / by the fstab edit-- then delete the /home reference in / (externally via a rescue disc)--after that--reboot.  If you are worried at all, burn the info in the Nautilus-seen /home to cd first--Sounds like you have a symlink---but why?

---

### Post by drizek on 2005-08-12
[QUOTE=autocrosser]That sounds kind'a like how I "saved" my user data from YellowDog when I installed Ubuntu---I installed Ubuntu on the / partition--then edited /etc/fstab to use /dev/hda3 as /tmp--/dev/hda4 as /home & /dev/hda5 as /opt (just how my system was set-up in YellowDog)--rebooted to a rescue disc & deleted the /home, /opt & /tmp directories from /---then booted into Ubuntu normally--had zero problems with doing it this way.

Check your /etc/fstab to see where your system "really" is--if you "really" have a seperate /home & it is as complete as the one you see in Nautilus--nuke the one in / by the fstab edit-- then delete the /home reference in / (externally via a rescue disc)--after that--reboot.  If you are worried at all, burn the info in the Nautilus-seen /home to cd first--Sounds like you have a symlink---but why?[/QUOTE]

its weird cause if i delete a file from the home in /, it deletes it in the home in hda6 as well. im pretty sure that if i delete /home in hda4, it will delete the /home in hda6 as well. also, for osme reason, i found unreal tournament on my / directory. i removed it, which freed up some space, but i still have no clue how it got there int hte first place. 

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               reiserfs notail,user_xattr          0       1
/dev/hda6       /home           reiserfs defaults,user_xattr        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda2       /media/windows  ntfs    nls=utf8,umask=0222 0   0
/dev/hda3       /media/hda3     reiserfs defaults,user_xattr    0       2

```

heres my fstab, pretty much the same as the one in Mepis, which did not have this problem.
Edit: i just noticed that my swap directory doesnt have a mount point. wtf? im pretty sure i installed/partitioned it correctly in the installer. its working fine on the other two pc's.


and df -h

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4              25G   24G  755M  97% /
tmpfs                 443M     0  443M   0% /dev/shm
/dev/hda6              56G   29G   27G  52% /home
/dev/hda2              28G   22G  5.4G  81% /media/windows
/dev/hda3             4.7G  2.7G  2.0G  58% /media/hda3
/dev                   25G   24G  755M  97% /.dev
none                  5.0M  2.8M  2.3M  56% /dev

```

Edit again, and WTF is that /dev thing in my df -h. why is it the same as my hda4?

---

### Post by autocrosser on 2005-08-12
Well-I'm at work right now, but I'll post my fstab this evening for you to look at--I think I'd burn the info on /home & edit fstab/nuke the /home & redefine /home afterwards---have you looked at both externally? 

I can work with my Linux partitions in OSX Mac as root user--easier to do it in a GUI way instead of command line. I format as ext3 instead of reiserfs because OSX has a way to see ext3--makes it simple to work on it from the outside ;-)

---

### Post by autocrosser on 2005-08-13
I don't have a idea why the /.dev is there--You could try deleting it & reboot--swap has no mountpoint in my system, so that looks ok--

My fstab---

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

I'm running four drives inside--hda-hdb-hdc & hdd--all can be worked with from Linux

---

