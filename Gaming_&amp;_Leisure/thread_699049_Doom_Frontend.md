---
title: "Doom Frontend"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by yizuman on 2008-02-17
Looking for a good Doom Frontend that launches doom and select wads of choice.

Don't need fancied up GLdoom or anything, just want a frontend doom launcher to play classic doom.

Any of that out there for ubuntu? (v7.10)

Thanks in advance....

---

### Post by SkonesMickLoud on 2008-02-17
Synaptic has lxdoom.  It came with the Doom 1 wad, but after some messing around, it now starts with Doom II.

I have no idea how I got the .wads to switch, so I can't help you there.

There's also Doom Legacy, which supports OpenGL:

[http://legacy.newdoom.com/](http://legacy.newdoom.com/)

I've had some trouble getting it to run with sound, and there doesn't seem to be an option to save games.

---

### Post by appleshampooid on 2008-02-17
I am also on the quest for a good Linux Doom engine.  I installed lxdoom, but the sound didn't work out of the box, the resolution was tiny, and using the `-2` option to double it resulted in semi-garbled graphics.

So I tried skulltag (had to install libfmod manually) and it was definitely better, but still with problems.  The window was about 2x the size of lxdoom but it would still be nice to have it full-screen.  The sound worked initially but it always quits about halfway through.  Also the gameplay is not as smooth as I would like.

This was the result of only a couple of hours' work...not sure if I want to try another engine or just try to tweak skulltag.

---

### Post by appleshampooid on 2008-02-17
I have tried skulltag out a little bit more and haven't been able to get through the first level of doom 1 without the game crashing...skulltag-crash.log says:
```

*** Fatal Error ***
Address not mapped to object (signal 11)
Address: 0x37fd

```

---

### Post by appleshampooid on 2008-02-17
> **appleshampooid said:**
> I have tried skulltag out a little bit more and haven't been able to get through the first level of doom 1 without the game crashing...skulltag-crash.log says:
```

*** Fatal Error ***
Address not mapped to object (signal 11)
Address: 0x37fd

```

Update on this specific crash - seems to be related to a specific map area.  It always crashes when I try to use the secret area in the first map of the first episode of doom 1 which gets you to the blue super armor.

---

### Post by appleshampooid on 2008-02-17
> **appleshampooid said:**
> Update on this specific crash - seems to be related to a specific map area.  It always crashes when I try to use the secret area in the first map of the first episode of doom 1 which gets you to the blue super armor.

Crashed again on a secret area on level 2 - pretty lame, dunno if my WAD is corrupted or what.

---

### Post by SnakeHips on 2008-03-13
I've just started using GZDOOM ,it works a dream with ultimate doom through wine and in opengl. I gave up trying to compile the others!

[http://grafzahl.drdteam.org/](http://grafzahl.drdteam.org/)

---

### Post by eragon100 on 2008-03-13
The combination prboom and freedoom, installable trough synaptic, woks great!
Sound, fullscreen, everything. Just no entire under games, so either make a shortcut somewhere or simply open a terminal and type prboom to play :)

---

