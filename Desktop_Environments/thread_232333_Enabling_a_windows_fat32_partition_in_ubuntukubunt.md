---
title: "Enabling a windows fat32 partition in ubuntu/kubuntu"
date: 2006-08-08
forum: Desktop Environments
---

### Post by sqlplus on 2006-08-08
Hi all,

New desktop linux user here, trying to making the transition, with the first of what I'm certain are many questions... 

I installed ubuntu and then kubuntu-desktop, thinking that I probably might prefer kde to gnome, although not for any particular reason, and I'm not necessarily commited either way yet.
  

Question that applies to both desktops: I have a fat32 partition that I would like to use to share docs between linux and my dual boot xp.  How do I have this partition be enabled/mounted automatically upon system startup?  

(a) In gnome I saw that I was enable to manually go into a gui dialog and enable the partition if I assigned it a mount point. This worked but I couldn't figure out how to make this happen automatically though upon startup.

(b) In kde, I see all my partitions if I go into sys admin | Disks and Filesystems, but I am not even able to "enable" the fat32 partition, let alone set it to be enabled on startup. The emable button is greyed out. This is true even after clicking on Administer Mode and entering my password.  (Possible issue - in kde I do not see the partition listed as being of type fat, while in gnome I did.)

So, how do I set things up so that I can access this partition? 
(a) via gnome
(b) via kde
(c) via the command line, and would this method be the same for both desktops?

Please feel free to point me to the docs or wiki if this is painfully obvious.

Thanks in advance!

---

### Post by Jagot on 2006-08-08
Here is the guide for you to mount and enable the FAT32 partition on boot:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532490](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html#id2532490)

Providing you mount properly you will be able to see and access the partition without having to do anything else.

---

### Post by sqlplus on 2006-08-08
Looks that that did it.  THANKS!!!

---

### Post by FenrisAbraxas on 2006-08-08
> **sqlplus said:**
> 
So, how do I set things up so that I can access this partition? 
(a) via gnome
(b) via kde
(c) via the command line, and would this method be the same for both desktops?

Please feel free to point me to the docs or wiki if this is painfully obvious.

Thanks in advance!

Hi, i'm a console man, so here it is.

```
 sudo gedit /etc/fstab
```

There you should have all the partitions in this format:

```
Logical Volume 	Mount Point 	FS type 	Options 	Dump 	Check order
/dev/hda1 	      / 	         ext2         defaults 	1 	1
/dev/hda5 	      /home 	      ext2         defaults 	1 	2
/dev/hda7 	      /tmp 	       ext2          defaults 	1 	2
/dev/hda6 	      /usr 	        ext2         defaults 	1 	2
/dev/hda8 	      swap 	      swap           defaults 	0 	0
/dev/fd0 	       /mnt/floppy   ext2            noauto 	0 	0
/dev/cdrom 	     /mnt/cdrom  iso9660             noauto,ro 	0 	0
```
Note: is all messed up i did a copy & paste from a website and im to lazy to adjust it. hope you get the idea :P

Look for the partition you want to load at boot time and add this extra option:

```
/dev/hda1    /mnt/something   vfat   auto,users,rw   0   0
```

That will tell fstab to load that partition at boot time, just adjust the settings to your system.

Good Luck

---

