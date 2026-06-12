---
title: "problem using stellarium in ubuntu8.10.helpme"
date: 2009-02-04
forum: Education &amp; Science
---

### Post by midhunse on 2009-02-04
hi,when i run stellarium i get the following

 -------------------------------------------------------
[ This is Stellarium 0.9.1 - [http://www.stellarium.org](http://www.stellarium.org) ]
[ Copyright (C) 2000-2008 Fabien Chereau et al         ]
 -------------------------------------------------------
File search paths:
 0. /home/midhun/.stellarium
 1. /usr/share/stellarium
Config file is: /home/midhun/.stellarium/config.ini
Sky language is en_US.
Application language is en_US.
Warning can't find module called  "StelUI" . 
Loading Solar System data...(loaded)
Loading star data...
Loading stars_0_0v0_1.cat: 0_0v0_1; stars: 5013
Loading stars_1_0v0_1.cat: 1_0v0_1; stars: 21999
Loading stars_2_0v0_1.cat: 2_0v0_1; stars: 151416
Loading stars_3_1v0_0.cat: 3_1v0_0; stars: 434064
ZoneArray::create( "stars_4_1v0_0.cat" ): warning while loading " "stars_4_1v0_0.cat" ":  file not found: stars/default/stars_4_1v0_0.cat 
ZoneArray::create( "mmap:stars_5_2v0_0.cat" ): warning while loading " "stars_5_2v0_0.cat" ":  file not found: stars/default/stars_5_2v0_0.cat 
ZoneArray::create( "mmap:stars_6_2v0_0.cat" ): warning while loading " "stars_6_2v0_0.cat" ":  file not found: stars/default/stars_6_2v0_0.cat 
ZoneArray::create( "mmap:stars_7_2v0_0.cat" ): warning while loading " "stars_7_2v0_0.cat" ":  file not found: stars/default/stars_7_2v0_0.cat 
ZoneArray::create( "mmap:stars_8_2v0_0.cat" ): warning while loading " "stars_8_2v0_0.cat" ":  file not found: stars/default/stars_8_2v0_0.cat 
finished, max_geodesic_level: 3
Loading location: "Paris", on Earth
Loading NGC data... (13226 items loaded [3175 dropped])
Loading NGC name data...( 222 names loaded)
Loading Nebula Textures for set default...(109 textures loaded)
Segmentation fault
midhun@ubuntu:~$ 

what is the problem? how to solve it?
pls anyone help me.

---

### Post by tapaswimakarand on 2009-02-05
Loading Constellation boundary data from /usr/share/stellarium/data/constellations_boundaries.dat... (782 segments loaded)
Loading star names from /usr/share/stellarium/skycultures/western/star_names.fab
Loading star sci names from /usr/share/stellarium/stars/default/name.fab
Loading Cities data for planet Earth...(2069 cities loaded)
Localizing TUI for locale: en_US
Localizing TUI for locale: en_US
Script completed.

This is the missing part. You may want to check whether those files exist. Another problem could be your graphics card. Stellarium requires pretty high graphics requirements. 

Regards

---

### Post by midhunse on 2009-02-05
ok, thankyou.i will try.

---

