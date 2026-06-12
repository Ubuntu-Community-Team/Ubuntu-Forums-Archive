---
title: "[SOLVED] quake 4 on start"
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by Homunculi on 2008-01-01
i need a little help with quake 4 ... 
i had quake 4 running for a while but i uninstalled it..
now there is 1.4.2 and i installed it and i get nothing 
i run quake 4 and i get : 
glprogs/heatHazeWithMask.vfp
glprogs/heatHazeWithMask.vfp
Error ERP_DROP: Joint 'chest' not found for 'joint_head' on 'ad_intro_char_marine_3'
TODO: Sys_SetClipboardData
------------ Game Map Shutdown --------------
---------------------------------------------
********************
ERROR: Joint 'chest' not found for 'joint_head' on 'ad_intro_char_marine_3'
********************
------------ Game Map Shutdown --------------
---------------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------


any help would be greatly appreciated
thank ya thank ya :guitar:

---

### Post by Homunculi on 2008-01-01
for got my system stats 

amd64 3800+
1gb 800mhz ram
2 320gb sata drives 
1sata dvd pioneer
1 ide plextor dvd
nvidia 7600gt pci-e

feisty fawn 7.04

---

### Post by BreathEasy on 2008-01-01
The first thing that comes to mind is perhaps not all of the PAK files have been copied over to their correct places. Here's a site which covers everything you need to know about installing Q4 in Linux:

[http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

---

### Post by Homunculi on 2008-01-01
i followed that guide ... and unles the files are corrupted 
i do not know what is wrong ....
i will try copying the files over again :guitar:

---

### Post by BreathEasy on 2008-01-01
BTW, in the folder which you've got all the files, run an md5sum against the pk4 files to make sure they are not corrupted.

From a terminal, type (and this assumes you installed in the default location):

cd /usr/local/games/quake4/q4base
md5sum *.pk4

As the values come out, make sure they exactly match the hash values shown below (they came from the link):

```
a9f6a2e4bf8e193591954f75d1d39f85  game000.pk4
b201b914167f47061fa5f975af527122  pak001.pk4
dabe2c88e004198947431250e3f4ca1d  pak002.pk4
8573f05af4c9568880cc464d06292079  pak003.pk4
12ff4006a7f7181ac16835d05c59905f  pak004.pk4
3576213f4e00f06baf3cd5de089a538a  pak005.pk4
aec7bb418b9a86256f9e5daee894dee2  pak006.pk4
0f53b4fb4df2c14fcd10012baf8b2f87  pak007.pk4
b099d75869f0ffcbcb8e5166374af345  pak008.pk4
cb2b44bf573559dc19b488d9e1e5bec3  pak009.pk4
d024073349dc917b4feab49e6abc417b  pak010.pk4
98c854d94ce1da5272952b77821823df  pak011.pk4
e77a2fda6656495d38773e05bbffda33  pak012.pk4
669d6d9a30b798d19434972475b98c53  zpak_english.pk4
```

If you don't get the exact same value for each file (and if any of the files listed above are missing from what you've got), then you'll have problems.

---

### Post by Homunculi on 2008-01-01
yep .. 
corrupted files .... 
thank you thank you .... 
:guitar:



rock on

---

