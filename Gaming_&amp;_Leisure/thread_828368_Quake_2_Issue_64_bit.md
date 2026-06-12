---
title: "Quake 2 Issue 64 bit"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by marioguy on 2008-06-13
I am on a 64 bit Ubuntu Hardy Heron installation I used the loki insaller and got it installed in my home folder.  It installed ok but when i try to run it i get this:
```
~$ '/home/max/quake2/quake2' 
Quake 2 -- Version 3.21+r0.16
using /home/max/.quake2/baseq2/ for writing
couldn't exec default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so") failed: No such file or directory
Refresh failed
recursive shutdown
Error: Couldn't fall back to software refresh!

```

---

### Post by Sleaka J on 2008-06-13
The library "ref_softx.so" is the software renderer as opposed to the OpenGL renderer, so if you're missing that it can draw anything on screen.

Try the following option:

./quake2 +set vid_ref glx +set gl_driver /usr/lib/libGL.so

to tell it to use OpenGL instead of the software renderer.

---

