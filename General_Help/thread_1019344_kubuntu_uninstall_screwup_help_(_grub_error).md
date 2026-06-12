---
title: "kubuntu uninstall screwup help ( grub error)"
date: 2008-12-23
forum: General Help
---

### Post by asgharjon on 2008-12-23
Hi, 

So basically i installed kubutu on my desktop, so it was
dual boot windows XP and kubuntu, being a beginner that i am , I just went to the DISK MANAGMENT part of the COMPUTER MANAGMENT in XP control panel, and selected the kubuntu partition and right clicked and deleted it ( bad online advice)

....

now all that comes up is GRUB ERROR 17, and i dont know what to do.....

help please, I tried to put in an ubuntu CD and fix it by reinstalling but it keeps freezing...

---

### Post by adult swim on 2008-12-23
you need to boot the xp cd and go to the recovery console.  then enter in ```
fixmbr

fixboot

exit 
```

---

### Post by Zorael on 2008-12-23
Or you could use a live cd. Boot it up to the desktop environment, enable the universe repository in Software Sources, then install the **testdisk** package (requires net connection). Run it with superuser permissions in a terminal, select your harddrive and pick Write MBR. (The partition table type is likely Intel, by the way.)
```
$ sudo testdisk
```
```
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
**[ MBR Code ]  Write TestDisk MBR code to first sector**
[ Delete   ]  Delete all data in the partition table
[ Quit     ]  Return to disk selection






Note: Correct disk geometry is required for a successful recovery. 'Analyse'
process may give some warnings if it thinks the logical geometry is mismatched.
```
If it says NO OPERATING SYSTEM when you boot up, you need to tag your Windows partition as Active in the Partition Editor, which is installed per default on live cds. (Alternatively in fdisk in a terminal.)

---

### Post by asgharjon on 2008-12-23
I tried what you said and it worked, it rebooted into XP automatically, thank you so much

---

