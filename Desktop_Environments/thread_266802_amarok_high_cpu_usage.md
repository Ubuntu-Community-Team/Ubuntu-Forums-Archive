---
title: "amarok high cpu usage"
date: 2006-09-27
forum: Desktop Environments
---

### Post by rwabel on 2006-09-27
Since I'm using latest amarok (2:1.4.3-0ubuntu6) my cpu usage is constantly around 100%

and top shows me:
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+ COMMAND
7357 rwabel    16   0  156m  62m  27m S 70.4  6.2  21:10.27 amarokapp


furthermore it takes quit a long time to exit the player. Anyone else noticed same behaviour?

---

### Post by orb9220 on 2006-09-27
Well without machine specs we don't know if this is normal for your machine.

Mine is a P4 1.3ghz with 640mb of ram. Amarok 1.4.3 and pushes my cpu% from around 8% to 30-40% at times. Amarok takes about 10secs to startup and same to shutdown.

Also if you don't have drivers for your video chipset installed this will greatlly affect your desktop usage and speed.

---

### Post by rwabel on 2006-09-28
AMD Athlon(tm) XP 2200+
1gb ram
nvidia GeForce 6600 GT with installed driver
everything was fine unless some days ago. Maybe it's also the latest version. Rebuilding the collection did also quit a bit now. it goes very seldom up to 100%. Everytime when a new song is played cpu usage gets high for a short moment. 

And in the past it didn't take that long to startup.

---

### Post by orb9220 on 2006-09-28
Well on my system I just rechecked and it is more like 20+ secs for startup and shutdown.

The increased times I think are due to the new dynamic playlist,collection thingy that was introduced in 1.4.2 or 1.4.3?

Check here to find out [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

---

