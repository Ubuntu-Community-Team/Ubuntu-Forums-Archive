---
title: "Partition resizing"
date: 2010-06-09
forum: Desktop Environments
---

### Post by nibblet5109 on 2010-06-09
Howdy all,

I'm trying to find out how to edit a partition.  I have windows and ubuntu installed side/side on my desktop, and I know I have to shrink the Windows partition to expand the Ubuntu one.  However, when I click edit partition in the Disk Utility menu, I get no option to do so.  I'm running 10.04 and Windows XP, sp2.  Any help would be greatly appreciated.

---

### Post by resolv_25 on 2010-06-09
Try something from [https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html](https://help.ubuntu.com/7.04/installation-guide/i386/partition-programs.html)
 Be careful if you are using *fdisk*.
If you are doing it for the first time, use some graphical programs.

Firstly, I would resize the partition from a windows, as I think you already did.
Then use this program and try to make a new partition or assign unpartitioned space to an existing partition.

---

### Post by helicase on 2010-06-09
Did you unmount your windows partition? You can't resize it when it is mounted.

---

### Post by nibblet5109 on 2010-06-09
I did mount the drive pre-initial attempt.  The only editing options I have ATM are labels and file type.  I also forgot to mention - I have no internet on the cpu in question, so I can't get extra programs on there to assist - I'm stuck with the disk utility.

---

### Post by Naggobot on 2010-06-09
Check Gparted live cd. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Also Ubuntu installation CD should have Gparted. 

Gparted is a tool to resize partitions but make sure that your Windows version is OK with resizing. I seem to remember some post about Windows 7 breaking if the partition is resized with anything other than approved tools what ever they are. 

I'll ad an edit if I find a relevant link

Edit: added above mentioned info, it seems that Gparted can be used with reservations if desired. 
Lots of info about partition resizing: [http://gparted-forum.surf4.info/viewtopic.php?id=13740](http://gparted-forum.surf4.info/viewtopic.php?id=13740)
Step by step instructions: [http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html](http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html)

---

### Post by Bobulous on 2010-06-10
I don't know what I was doing wrong, but I could not get gparted or Disk Utility to increase the size of a pair of partitions used for RAID.

Bizarrely, gparted was happy for me to simply delete both partitions (make sure to do a backup of all files, and check that the backup contains everything). Then I just asked Disk Utility to create me a new RAID 1 array and all was good (after a bit of readjusting the /etc/fstab).

---

### Post by gingivere0 on 2010-06-10
First, defrag your windows partition using Perfect Disk.  [www.perfectdisk.com](www.perfectdisk.com)
It *will* take quite a long time to defrag if this is your first time.  (It took me nearly 2 hours on an almost clean install) Do this a few times and then go to the control panel and look for Administrative Tools.  Then Computer Management, then Disk Management on the left.  Then right click on your windows partition and click on shrink partition.  Your partition can only be shrunk as far as the last file in the windows partition.

---

