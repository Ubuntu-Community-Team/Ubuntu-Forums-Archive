---
title: "can I still have GRUB menu on boot using two harddrives?"
date: 2008-12-13
forum: General Help
---

### Post by scalywag66 on 2008-12-13
I recently got Ubuntu 8.04 a few months ago, fell in love and ended up installing on my 80GB harddrive. As updates came for Ubuntu and were installed, including 8.10 upgrade, my GRUB menu got flooded with various Ubuntu startups and they have become pretty much useless. The most recent Ubuntu startup entry (Ubuntu 8.10 v29.5 .... or something) hangs on up boot up and never does so, and the other Ubuntu entries start up normal, but just about all services fail to work and I kept getting some message about "Power Management wasn't installed properly etc., ....".
 
So I left it alone for a bit and kept browsing for help on XP online. A few days passed and I came up on a second harddrive that holds 160GB and installed it onto my machine with no prob. Throughout my browsing for help, I came across Ubuntu Ultimate Edition and was glancing it's website when my eyes and mind subconciously caught the phrase "gamer's edition" which triggered an instinctal reaction for which I was then compelled to head over to the download area and do the do(pretty huge file).
 
After a succesful download and .iso burn, I ended up installing it on the entire second drive and was in geek orgasmic heaven as I toured 'teh Ultimate'. When I restarted the machine, I noticed that Ultimate wasn't inserted into the GRUB menu(tho i think i know why ... dif harddisk) and realized that in order to get to Ultimate, i hate to set 2nd drive as main disk boot up in BIOS. Since my 2nd drive is now going to be my main drive for Ultimate, I'd like to uninstall Ubuntu 8.10 and retrieve the memory from the first drive for XP usage, but would like to have a GRUB menu to choose from SDA or SDB. It really isn't that much of a hassle to change disk boot up thru BIOS I suppose.
 
I installed on the default 80GB harddrive(partitioned in two) that came with my machine like so
 
C: 15GB (Windows XP)
D: 65GB (25GB Windows XP / 40GB Ubuntu)
----------------------------------------------------
G: 164GB (Ubuntu Ultimate Edition)
 
 
When I am on Ubuntu on the first drive, I see other partitions were made on the dates that I updated/upgraded. So now D: is ...
 
D: 65GB (25 Windows XP / 10GB Ubuntu / 15GB Ubuntu / 15GB Ubuntu) 
 
My sorry as must've done something stupid that disabled the other Ubuntu startup entries and is prolly why my GRUB is flooded with 5 versions on Ubuntu to startup. To add to it, when I first installed Ubuntu, I did so inside of XP but uninstalled it before installing using the Live CD. So even when I choose Windows XP from GRUB, I have to choose XP again from another menu of Ubuntu/Windows XP.
 
So, how can I uninstall Ubuntu from the first drive and can I have a GRUB menu to choose from both harddrives?

---

### Post by logos34 on 2008-12-13
you might want to post 

sudo fdisk -l

But I think you can just add an XP entry to ultimate grub like this:

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by scalywag66 on 2008-12-13
Don't laugh at me to much,  I know I messed up

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf18342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1462    11743483+   7  HPFS/NTFS
/dev/sda2            1463        9729    66404677+   f  W95 Ext'd (LBA)
/dev/sda5            1463        4429    23832396    7  HPFS/NTFS
/dev/sda6            4430        5718    10353861   83  Linux
/dev/sda7            9487        9729     1951866   82  Linux swap / Solaris
/dev/sda8            9200        9465     2136613+  83  Linux
/dev/sda9            9466        9486      168651   82  Linux swap / Solaris
/dev/sda10           5719        9050    26764258+  83  Linux
/dev/sda11           9051        9199     1196811   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cdd150c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19836   159332638+  83  Linux
/dev/sdb2           19837       20023     1502077+   5  Extended
/dev/sdb5           19837       20023     1502046   82  Linux swap / Solaris

```

---

### Post by logos34 on 2008-12-13
yep, looks like sda1 is your windows c: system partition.  So edit menu.lst per the example in the link I gave you

---

### Post by caljohnsmith on 2008-12-13
If you want to uninstall Ubuntu from your 80 GB drive, you could simply delete all of its partitions. Then you can use that space to create one or more data partitions or whatever you want. As long as just Windows is going to be on that drive, I would recommend installing a Windows MBR to that drive so you will be able to boot that drive in case something happens with your other drive. You can install a Windows MBR from the terminal (Applications > Accessories > Terminal) by doing:
```
sudo lilo -M  /dev/sda mbr
```
Also, to boot Windows from your sdb drive, first open up the menu.lst in your Ultimate Ubuntu:
```
gksudo gedit /boot/grub/menu.lst
```
And add at the end:
```
title       Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And that should work assuming you don't have any issues with Windows. How about giving that a shot and let me know how it goes. :)

---

