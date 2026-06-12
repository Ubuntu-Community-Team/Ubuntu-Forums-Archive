---
title: "choppy sound in quake2"
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by TuxicGuy on 2005-10-26
Hi all,
     I've just recently installed Quake2 on breezy - evrything works except that the sound is very choppy - can anyone suggest a fix for this? Thanks in advance 

TuxicGuy

---

### Post by seethru on 2005-10-26
I personally haven't tried quake 2, but for the id games I do have installed, before I got hardware mixing, using the variable +set s_device oss seemed to fix the alsa issues.

---

### Post by TuxicGuy on 2005-10-28
OK.. I fixed this problem by setting snddriver as sdl and snddevice as /dev/dsp
in config.cfg - also did a chmod 666 /dev/dsp so that it could be written to easily! - I hope this helps someone else having the same problem - Thanks seethru for the assistance

---

### Post by Skatox on 2005-11-05
I'm running with the command 'aoss quake2' but it sucks, can you tell me what sound are you using in linux? alsa, esd or oss? cause sdl don't work for me. O tell me if you did something apart.

---

### Post by frogotronic on 2008-01-18
```
quake2 +set snddriver ao +set snddevice oss
```

---

