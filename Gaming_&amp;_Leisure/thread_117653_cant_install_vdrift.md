---
title: "cant install vdrift"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by maccom on 2006-01-15
i have downloaded bother source and binary for the latest version of Vdrift

to install it i need openal installed but i cant seem to install it.

i cd to its dir, ./configure thats fine
i type make
and get the following error::

> arch/arts/arts.c:230: error: 'ARTS_P_BUFFER_SIZE' undeclared (first use in this function)
arch/arts/arts.c:231: error: 'ARTS_P_BLOCKING' undeclared (first use in this function)
make[2]: *** [libopenal_la-arts.lo] Error 1
make[2]: Leaving directory `/tmp/openal-0.0.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/openal-0.0.8'
make: *** [all] Error 2


---

### Post by Mr_Grieves on 2006-01-15
What I can see this seems to be sound related. What sound driver do you run?
Make sure you have an uptodate sound driver that works for you're card.

---

### Post by maccom on 2006-01-16
i cant get no sound from my speakers. i have a (PCI) sound blaster live! 24-bit

---

### Post by Harleen on 2006-01-16
This is not sound card problem. This will occure only when you run that game, not while compiling.
The compiler complaines about some undefined constants/variables. But you run ./configure before, just to ensure you have everything you need installed. If configure finishes whithout any error, compilation should also run. If it doesn't (as in you case) I would assume either a bug in the source code (unlikely for that message) or a bug in the configure script.

That error message has something to do with Arts, the KDE soundserver. If you don't use it, you can try to compile openal without Arts support by calling "./configure --disable-arts" or something like that. "configure --help" will give you the right option for that.

---

### Post by go_beep_yourself on 2007-12-09
> **Harleen said:**
> This is not sound card problem. This will occure only when you run that game, not while compiling.
The compiler complaines about some undefined constants/variables. But you run ./configure before, just to ensure you have everything you need installed. If configure finishes whithout any error, compilation should also run. If it doesn't (as in you case) I would assume either a bug in the source code (unlikely for that message) or a bug in the configure script.

That error message has something to do with Arts, the KDE soundserver. If you don't use it, you can try to compile openal without Arts support by calling "./configure --disable-arts" or something like that. "configure --help" will give you the right option for that.

Is arts required to have sound in the game? I am running the game in gOS Ubuntu, and I have no sound. I tried running it with aoss and had the same results.

---

