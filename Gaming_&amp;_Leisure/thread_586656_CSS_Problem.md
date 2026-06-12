---
title: "CS:S Problem :/"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by Haydar on 2007-10-22
CS1.6 works perfectly but when i'm trying to play CS:S i can see it's starting up but it shoots me back to the desktop how can i fix this :<




OS : Ubuntu 7.10
Wine version : wine-0.9.47

FGLRXINFO
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6473 (8.37.6)

System specs :

Amd athlon 2800+
Radeon 9600
Creative soundblaster audigy
MX518
1024DDR RAM
Sennheiser PC160

---

### Post by karth on 2007-10-22
I'm not sure what's your wine setup and you may know this already, but Wine has an interesting virtual desktop nesting feature: your app runs in a "Wine desktop" and that virtual space is used as the viewport.

I heard and experienced that many fullscreen games are causing freezes or X crashes, and checking that option can solve many problems (under winecfg > Display > Use virtual desktop, and specify the default resolution).

You can set the standard resolution of your virtual desktop, it'll be eventually resized if needed by the game you're running.

---

### Post by Haydar on 2007-10-22
woops double post

---

### Post by Haydar on 2007-10-22
> **karth said:**
> I'm not sure what's your wine setup and you may know this already, but Wine has an interesting virtual desktop nesting feature: your app runs in a "Wine desktop" and that virtual space is used as the viewport.

I heard and experienced that many fullscreen games are causing freezes or X crashes, and checking that option can solve many problems (under winecfg > Display > Use virtual desktop, and specify the default resolution).

You can set the standard resolution of your virtual desktop, it'll be eventually resized if needed by the game you're running.

Already tried that it still shoots me back to the desktop

---

