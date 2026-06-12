---
title: "Alien Arena 2008 consistently crashes at same level ???"
date: 2008-05-17
forum: Gaming &amp; Leisure
---

### Post by mjiba on 2008-05-17
Since I upgraded to Hardy, Alien Arena crashes when trying to load the third level (in single player).  
Here is a small snippet of the output in terminal:

The Blood Factory
*** stack smashing detected ***: /usr/lib/games/alien-arena/crx.sdl terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ba3138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7ba30f0]
/usr/lib/games/alien-arena/crx.sdl[0x80d0814]
/usr/lib/games/alien-arena/crx.sdl[0x80b442c]

there's a lot more after this message, but I don't want to post TONS of output if it's not necessary.  Anybody have an idea what is going on here???

---

### Post by N05F3R4TU on 2008-05-23
I'm having the exact same problem. I'm not sure what the error message is, but it consistently crashes on attempting to load The Blood Factory. I have all the video settings at minimum, meaning all the options are disabled (shaders, shadows, etc.) Other than that, a standard install on Ubuntu 8.04 32 bit.

---

### Post by Irritant on 2008-05-23
There is a fix for it in SVN.  If you're not using SVN, in the source file source/ref_gl/r_model.c replace the declaration "char tmp[16]" with "char tmp[MAX_QPATH]".  This is found in the function Mod_LoadBrushModel at line 1196.  Recompile, and you should be all set :)

[http://svn.icculus.org/alienarena/trunk/source/ref_gl/r_model.c?r1=808&r2=929](http://svn.icculus.org/alienarena/trunk/source/ref_gl/r_model.c?r1=808&r2=929)

---

