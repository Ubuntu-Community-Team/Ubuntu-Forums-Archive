---
title: "No Sound in TuxKart"
date: 2005-07-24
forum: Gaming &amp; Leisure
---

### Post by Olrich on 2005-07-24
I have sound working in most other applications (XMMS, Totem, some games) but whenever I open TuxKart, and a few other games, sound fails work.  The error message from TuxKart is as follows 

slDSP: open: Device or resource busy
WARNING: slScheduler: soundcard init failed.

I had read in an earlier thread that some people fixed a similar problem by uinstalling libsdl-oss and installing libsdl-all but this had no effect.  I tried replacing Esound with Polypaudio, which also had no effect.  If anyone has any insight on how to fix this problem it would be greatly apprecieated.

Thanks.

EDIT: After a little bit more research it seems as if this is a plib problem. But, I still don't know how to fix it.  I tried reinstalling plib, but that again had no effect.  Thanks again.

---

### Post by NeoChaosX on 2005-07-24
Kill either the esd or polypaudio server, whichever one you're running. Any sound servers running automatically shut off sound in TuxKart, for some reason.

---

### Post by Olrich on 2005-07-25
Thank you, that fixed the problem.

---

### Post by akwatve on 2008-03-13
I am facing same problem
I dont have esd or polypaudio running...

supertuxkart gives following errors

 supertuxkart
Data files will be fetched from: '/usr/share/games/supertuxkart/'
slDSP: open: Device or resource busy
WARNING: slScheduler: soundcard init failed.
WARNING: Could not initialize the PLIB based sound.
Highscores will be saved in '/home/alok/.supertuxkart/highscore.data'.

---

