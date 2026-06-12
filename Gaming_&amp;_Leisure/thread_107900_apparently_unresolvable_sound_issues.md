---
title: "apparently unresolvable sound issues"
date: 2005-12-24
forum: Gaming &amp; Leisure
---

### Post by ZomCoder on 2005-12-24
hi everyone,

I can get sound working with:
ppracer
slune
quake3

but ONLY when I type
aoss ppracer
aoss slune
etc...

doomsday ALSO does work with 
aoss doomsday

HOWEVER...the sound is laggy (ONLY on doomsday).

How the heck do I set up ALSA so that I don't need oss? I've combed this forum with as many search combinations as I can think of and I just can't find any previous posts on this issue.

It has been reccommended to me to install various pre-done packages and I have tried this, but I am inexperienced with linux: perhaps my compiled versions are still overriding the packages? Perhaps I should just reinstall ubuntu at this point and try nothing but packages. But that's lame...I was able to compile & install MPlayer flawlessly.

Thanks so much!
-Zom.

---

### Post by cdsboy on 2005-12-24
try running them in root. thats what i have to do for quake3 and Return to Castle Wolfenstien...

---

### Post by ZomCoder on 2005-12-24
Running these games in root had no effect; aoss was still necessary for sound to work.

It is only doomsday which has a problem when running with aoss, everything else sounds/looks great.

I tried loading some sound modules directly as root, but this did not resolve the problem either.

note that doomsday DOES have sound when running with aoss, it is just very laggy.

---

