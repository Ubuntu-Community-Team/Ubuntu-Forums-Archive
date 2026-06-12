---
title: "No sound with Enemy Territory"
date: 2006-08-30
forum: Gaming &amp; Leisure
---

### Post by atriste on 2006-08-30
Hi, 

i am running Dapper Drake and just installed enemy territory, 

as usual i had no sound so i tried the method that has worked before in terminal: 

sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

however it said i did not have permission, 

so i looked around and saw things such as 

et + set s_driver oss 

and i had no luck, 

then i tried to configure the sound using the method described on the dapper wiki, and it didn't help any

then i tried: 

sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit

and i still have had no results, 

any suggestions on how to get it working?  

my sound works perfect in everything else so far, quake 4, cds, dvds and what not  

thanks for any help

---

### Post by DoktorSeven on 2006-08-31
Shut down all programs that make sound then:
(if using gnome)
killall esd 
(if using kde)
killall artsd

---

### Post by kvonb on 2006-08-31
See my fix in this post:

[http://ubuntuforums.org/showthread.php?t=167679](http://ubuntuforums.org/showthread.php?t=167679)

Regards,

Kev :)

---

