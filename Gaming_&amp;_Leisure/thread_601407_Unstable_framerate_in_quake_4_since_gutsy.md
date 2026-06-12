---
title: "Unstable framerate in quake 4 since gutsy"
date: 2007-11-03
forum: Gaming &amp; Leisure
---

### Post by Benjamin_Vedder on 2007-11-03
Since i installed gutsy 7.10 the framerate in quake 4 went unstable. It is 30 to 60 fps no matter what i do with the settings. Even in the menus its the same.  With 7.04 the framerate was 59 to 61.

My hardware is: Pentium D 960 3.6 ghz, GeForce 7900, 4 gb ddr2 ram. I use the 100.14.19 driver installed with envy.

It is the same on my laptop with 7.10. Unstable framerate in quake4. Hardware: GF8600gt, core2duo, 2 gb ddr2ram.....

Do i have to go back to 7.04 or is there some way to solve this?

This is my xorg.conf (had a lot of trouble with the screen resolutions as you can see, and the moment it worked i just left i as it was)

EDIT: Removed it since its not important anymore.

Edit: Im at hardy now with new drivers, settings, hardware etc. and the problem still remains. See later posts for more details.

---

### Post by Benjamin_Vedder on 2007-11-03
ok, reduced my xorg.conf to this and still the same problem...

Edit: This one is also out of date, i can post my current config, game config etc. if that is important.

---

### Post by Mblackwell on 2007-11-03
Did you disable desktop effects?

---

### Post by Benjamin_Vedder on 2007-11-03
Yes, of course...

---

### Post by Benjamin_Vedder on 2008-02-01
Just to let you know.. i didnt solve this under the 32-bit version of ubuntu 7.10, but the 64-bit version works just fine. even compiz fusion runs faster under the 64-bit version. so if you have similar problems, try it

---

### Post by eljoeb on 2008-02-01
Have you tried commenting out the composite line?

---

### Post by Benjamin_Vedder on 2008-02-02
metacity --replace, but the thing is, everything else worked fine just not quake 4, and i have confirmed this on my laptop too. But it runs faster with the 64-bit version (i know that i have no desktop effects when i run games).   Compiz still runs slow on my laptop when i run it, even i have all mipmaps turned off, framerate set too 200 fps, loose bindings, no vsync, direct rendering etc. Not all effect are slow, only the animations. I also confirmed they run faster with gtk window decorator then emerald. But still, 7.04 was faster with the effects and even with that game without effects. I would like to run it on my laptop, but my wlancard makes the system freeze when i download or upload files too fast. there is even a bug report about that with ndiswrapper, a lot of people experience that.

---

### Post by Benjamin_Vedder on 2008-02-03
Ah, that line.. yes i have, but that config is out of date now :P I also have new hardware and new drivers since i posted that

---

### Post by Benjamin_Vedder on 2008-03-23
I have tried hardy now and even the 64 bit version has this problem. I have checked other forums and it seems other people have similar problems. Here are some examples:

[http://www.nvnews.net/vbulletin/showthread.php?t=81682&highlight=quake4+fps]("http://www.nvnews.net/vbulletin/showthread.php?t=81682&highlight=quake4+fps")
Edit: this is exactly what happens on my system too.

[http://www.nvnews.net/vbulletin/showthread.php?t=60396&highlight=quake4+fps]("http://www.nvnews.net/vbulletin/showthread.php?t=60396&highlight=quake4+fps")

[http://www.nvnews.net/vbulletin/showthread.php?t=88319&highlight=quake4+fps]("http://www.nvnews.net/vbulletin/showthread.php?t=88319&highlight=quake4+fps")

Other games run fine, just not quake 4, and i have no clue at all. The menus cant keep up with the framerate either, even if i dont load any game. 

Current info about my system and hardware::

Laptop:
gf 8600gt
Nvidia 169.12 driver
Hardy 32 bit
(desktop effects disabled of course)
vsync disabled in the nvidia-settings and in the game

Desktop: Same as above but 64 bit hardy and gf 7900gs card.

The same problem on both. I have tested a lot of different settings in the game with sound driver, multicore support, resolution, different gameversions etc. Allways the same problem.

I dont play quake 4 that much, but it doesnt feel right not having that game working since i spent money on it.

Thanks for ideas and help

---

### Post by Benjamin_Vedder on 2008-03-25
Bump.

---

