---
title: "GParted not showing partitions"
date: 2009-04-07
forum: General Help
---

### Post by samurai_47 on 2009-04-07
my system is setup as follows

139gb - Win 7
50gb - ubuntu 8.10
2gb - swap space
58gb - fat32 - for OSX, not yet installed

in windows 7 i used acronis to resize windows from 185gb to 139gb, i when to GParted to format the fat32 partition and it shows the HDD but none of the partitions, though i can still mount them and access the files on them.

what would be causing this?, its no problem if it cant be fixed, my system still runs fine.

thansk

-samruai_47

---

### Post by ajmctaggart on 2009-04-07
Top right corner of gparted only shows one partition in the drop down too?

If so that is pretty strange...I wonder if was the Windows partition app?  

Try booting off a Live Cd from whoever and see what it does...if you're curious enough :)

---

### Post by samurai_47 on 2009-04-07
yeah gparted only shows the HDD as one partition, oh and i notcied that it says the entire thing is unallocated. btw what do you mean by boot off a live cd? ill try booting off of my Ubuntu Live USB and see what happens, or should i go up the partition editor in the install process?

thanks for the help.

-edit-
oops i forgot, my USB startup disc is corrupt and i dont have access to my ubuntu discs now

---

### Post by ajmctaggart on 2009-04-08
Did you usb stick get corrupted while you were installing?  Just curious if that has anything to do with your damaged partition table.  More than likely, your partitions are correct, but for some reason they aren't being read correctly.  

Can you post the contents of /etc/fstab here?

Thanks,

---

