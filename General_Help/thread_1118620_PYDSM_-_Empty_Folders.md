---
title: "PYDSM - Empty Folders"
date: 2009-04-07
forum: General Help
---

### Post by Ordes on 2009-04-07
I tried to figure out automounting NTFS partitions in ubuntu. And i came along PYSDM. The basic i figured out. But some of my folders appear "empty".

Detail: I have 2 storage HDD
Hdd1 -> "Storage"  (sdb1)
Hdd2 -> "Storage2" (sdc1)

Before PYSDM, after mounting Storage2, i could just browse through it, or /media/Storage\ II; worked fine

After installing PYSDM:
All Hdd are automounted
1.) After startup "Storage II" appears on the desktop, and in nautilius on "Storage II" i can browse it
2.) in /media/ i now have sdc1 and Storage II
    --> /media/sdc1/ and i actually have all my data
    --> /media/Storage\ II/ appears empty

Is there any way to change this back, like before media only contained: cdrom, Storage Stroage II etc, now its this, plus sdb1 sdc1 etc

Also all the applications that had folders in Storage II. e.g Picasa, Amarok, Rainlendar, couldnt find the data anymore, so i need to reconfigure all, unless i can reset this

Or in Amarok file browser, when i go media/storage II its empty, so i have to go sdc1 .....

Tried to change the NAME in PYSDM, but the results were the same as above.

thanks for advice

-----

PS: i also tried NTFS config, but it only recognized my sda1, and didnt find sdb1 sdc1. Any clue? thats the reason why i tried PYSDM

---

### Post by Ordes on 2009-04-07
Mhm

Or is it because Storage II is a DIR, that had been used before to mount, and  therefore is still in /media/ ,but not used anymore. And the new DIR is now sdc, etc.

When it is like this, couldnt I? :
1. rm -r Storage II
2. use PYSDM sdc1 rename to Storage II

Because when i want to name sdc1 to Storage II right now (in PYSDM) it gives me an error. which is kind of obvious as i already have a /media/Storage\ II 

Any Ideas to this? txs

---

### Post by Ordes on 2009-10-14
removed PYSDM, learned how to use fstab, everything working fine now

it seems for some stuff if you do it manually it actually works better

---

