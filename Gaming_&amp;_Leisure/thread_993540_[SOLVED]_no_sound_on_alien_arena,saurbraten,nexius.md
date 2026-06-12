---
title: "[SOLVED] no sound on alien arena,saurbraten,nexius?"
date: 2008-11-25
forum: Gaming &amp; Leisure
---

### Post by rixtr66 on 2008-11-25
Im running ubuntu studio,and the sound works fine on all applications except
games?is there a sound dependency for these games that im missing ?
i find this strange because ubuntu is usually very thuorough with dependencies.any help would be appreciated!!!
Rick

---

### Post by sheeva on 2008-11-26
Maybe you should try to the add/remove and look for ubuntu restricted extras. 

this should enable mp3, dvd, and flash and others

---

### Post by eragon100 on 2008-11-26
> **sheeva said:**
> Maybe you should try to the add/remove and look for ubuntu restricted extras. 

this should enable mp3, dvd, and flash and others

That could hardly be the cause of this problem, as these games ship with music in OGG format, AFAIK.

Install the alsa-oss package:

sudo apt-get install alsa-oss

restart the computer. You don´t have to anything else, it should be fixed now. If it still doesn´t work, feel free to post again! :wink:

---

### Post by rixtr66 on 2008-11-26
ok i installed the alsa oss package and that worked!
thanks!!! i should have thought of that.
anyway thanks again.
Rick :)

---

### Post by eragon100 on 2008-11-26
> **rixtr66 said:**
> ok i installed the alsa oss package and that worked!
thanks!!! i should have thought of that.
anyway thanks again.
Rick :)

You're welcome

---

