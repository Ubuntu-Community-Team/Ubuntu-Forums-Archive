---
title: "snes9x-gtk hardware acceleration issue"
date: 2010-04-03
forum: Gaming &amp; Leisure
---

### Post by megamaced on 2010-04-03
Hi,

When I enable hardware acceleration (xvideo) option in snes9x-gtk I lose the game graphics completely.. either whole application just vanishes apart from the menu at the top.. If I use a software renderer it works fine but performance is pretty bad.

Some info:

Karmic 64 bit
ATi Radeon 3200 HD IGP (using proprietary driver)
snes9x gtk version 79 (snes9x version 152)

I do not have this issue using hardware accel on Gens/GS or PCSX-df. I haven't tried zsnes yet but I prefer snes9x

Cheers

---

### Post by megamaced on 2010-04-07
Nevermind, I worked it out... the deb in the getdeb repo is weird..

I got the deb from the "official" ppa and now I have an "openGL" option :)

---

