---
title: "Blender borked"
date: 2012-09-18
forum: Desktop Environments
---

### Post by madtom1999 on 2012-09-18
Got a 4core machine but blender loads excruciatingly slowly (15s) and then takes 10s to drop down the file menu, ditto to get to user preferences and then that locks up but can be closed.

---

### Post by mcduck on 2012-09-18
Application loading time pretty much depends on your hard drive performance, not processor cores or speed.

...and Blender draws all of it's user interface usign OpenGL, so a decent graphics card and properly workig drivers for it are essential. So make sure your graphics drivers are workign correctly as well.

Also, if you are usong the Blender version from Ubuntu's repositories, I recommend trying the latest version from blender.org instead. It's ready to run, so all you have to do is download and extract somewhere, no compiling required. :)

If you still ahve problems after checking thos ethings, try running Blender from a terminal so you can catch any error messages it might give.

---

### Post by madtom1999 on 2012-09-18
Thanks - its not disk  - that runs like the wind. Almost everything else is lighning fast. OpenGL tests return almost everything>100fps
It is a repostory download - I'll try a blender site version.

---

### Post by madtom1999 on 2012-09-18
Just tried the new one - the same
I'm using Nvidia drivers and tried changing those about - no luck

I get the following error in a console:
WM: failed to allocate texture for triple buffer drawing (glGenTextures).

---

