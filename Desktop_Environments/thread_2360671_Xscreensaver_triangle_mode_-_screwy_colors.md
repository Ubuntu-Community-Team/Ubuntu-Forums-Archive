---
title: "Xscreensaver triangle mode - screwy colors"
date: 2017-05-06
forum: Desktop Environments
---

### Post by kingv2 on 2017-05-06
Alright, I remember back in the days when I worked on SunOS/Solaris workstations in the late 90s, xscreensaver (then called xlock, I believe) had various modes.

Galaxy and Triangle were among my favorites.

So, I have them both on my current machine, Lubuntu 17.04, but Triangle is a bit screwed up.  The colors are bizarre.  I've tried tweaking the options, to no avail.

When it used to run on the old Sun/Solaris machines I had, the flat area, basically water surface, was always a good, solid blue, and the mountain/landscape would be various colors, but something you might expect to see, greens, yellows, some reds/oranges, etc.  But, when I use it now, the colors are random, and quite jarring, and it picks a different set of colors each time it starts a new triangle.

The only thing I've come across was on this page:  [https://fossies.org/linux/xlockmore/modes/triangle.c](https://fossies.org/linux/xlockmore/modes/triangle.c) - it's apparently the source code, and I noted the following line:

#define UNIFORM_COLORS /* To get blue water uncomment, but ... */

However, I'm not looking to dig into the system and recompile code.  Is there some way to get this to work in the current system as-is?  Or does this really have to be rebuilt, and then I replace the result in /usr/lib/xscreensaver/triangle?

---

