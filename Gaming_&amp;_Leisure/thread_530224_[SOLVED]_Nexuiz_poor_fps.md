---
title: "[SOLVED] Nexuiz poor fps?"
date: 2007-08-20
forum: Gaming &amp; Leisure
---

### Post by kipman725 on 2007-08-20
Hello I have:
ATI x1950pro (AGP)
3400+ sempron (754)
1GB DDR3200
ubuntu 7.04 64bit

My openGL performance dosen't seem to be very good, I have installed the driver from the restricted devices manager for 3d acceleration.  In nexuiz I get barely playable fps going from 90 to the mid teens at medium textures, all effects turned down and 1280x1024.  IN glxgears I get 4k fps when the window isn't in the foreground and only 280ish when it's in the foreground.

I know the ATI drivers are poor but shouldn't I have better performance than this?

---

### Post by GFree678 on 2007-08-20
The DarkPlaces engine (which is what Nexuiz uses) can be tempremental. First off, make sure you're not running Beryl or Compiz, as Nexuiz seems to be more effected by them than some other games I've tried.

Also, check the graphical options you've enabled. HDR can be a killer, and world shadowing will DESTROY your frame rate. Play around a bit and see how things work out.

---

### Post by kipman725 on 2007-08-20
well I turned everything to minimum on nexuiz (settings that play fine on a geforce 2 ultra in  one of my pcs) and still fps dipping to 22ish.  I also tried the 64bit version of ut2004 demo and that had such bad fps it was jerky in the menus and the game ran at about 5fps.  3d acceleration is working just very very slowly, any ideas?

*wow my sig is out of date :P

---

### Post by tk471 on 2007-08-21
I run Nexuiz 2.3 on Ubuntu Studio 32bit with 768MB PC2700, 2.0Ghz AMD Athlon XP, NVidia 6200, Diamondmax 5.1 audio (I just woke up so I'm trying to remember off the top of my head hear), and I have resolution set to 1024x768 in the game, most effects off, but OpenGL 2.0 shaders on, I get anywhere from 40 to 100 fps depending on the map and how much action is going on.

Are you running Nexuiz 2.2.3 from Ubuntu repository, or 2.3 latest from Nexuiz folks?  Have you tried to lower your in-game resolution?

---

### Post by kipman725 on 2007-08-21
I think i have traced the problem to my AGP port been stuck at 0x speed.  Quite annoying as it afflicts both windows and ubuntu after my recent format (I think the newer ATI drivers are incompatible with my motherboard).  SO I will list this as solved thanks for the suggestions.

---

