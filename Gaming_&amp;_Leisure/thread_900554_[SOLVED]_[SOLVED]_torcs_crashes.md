---
title: "[SOLVED] [SOLVED] torcs crashes"
date: 2008-08-25
forum: Gaming &amp; Leisure
---

### Post by nisaky on 2008-08-25
I played torcs on my brother's laptop and i seen it is good game. I decided to install it on my new computer (AMD 64 X" 5600+, 500 GB hard disk, nVIdia 8600 GT 512 MB, 4 GB RAM....it's good enought) and game starts normaly. 

But when i click on "Configure Player" it crashes and writes:



"yasha@yasha-desktop:~$ torcs
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
parseXml: not well-formed at line 96
gfParmReadFile: Parse failed in file "/home/yasha/.torcs/drivers/human/preferences.xml"
/usr/games/torcs: line 52:  9143 Segmentacijska gre&#353;ka  $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*"



If i click on any race it starts loading and crashes, writing:



"Compatibility mode, properties unknown.
parseXml: not well-formed at line 96
gfParmReadFile: Parse failed in file "/home/yasha/.torcs/drivers/human/preferences.xml"
WARNING: grscene:initBackground Failed to open shadow2.rgb for reading
WARNING:         no shadow mapping on cars for this track 
parseXml: not well-formed at line 96
gfParmReadFile: Parse failed in file "/home/yasha/.torcs/drivers/human/preferences.xml"
/usr/games/torcs: line 52:  9034 Segmentacijska gre&#353;ka  $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*"



How can i fix it???? All other games work fine on my PC.

---

### Post by nisaky on 2008-08-27
I would really like to see answer...

---

### Post by nisaky on 2008-08-28
Thanks for answer....

---

### Post by spoons on 2008-08-28
I haven't had this problem on Linux or XP. Have you tried contacting the TORCS developers themselves?

---

### Post by nisaky on 2008-08-29
problem solved. I deleted my .torcs folder in home and it solved it. Probably i did something bad n configurations :S

---

