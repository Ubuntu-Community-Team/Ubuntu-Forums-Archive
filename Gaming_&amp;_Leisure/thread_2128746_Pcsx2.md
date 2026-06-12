---
title: "Pcsx2"
date: 2013-03-24
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2013-03-24
Hi there,

I just downloaded the PCSX2 version 1.0.0, using the Gregory PPA (official Ubuntu PPA?).

I've been running into some hiccups. Specifically with the plugins. The two games I am trying with right now are Kingdom Hearts 2 and Burnout 4: Revenge.

**_Graphics Performance/Problem:_**
Everytime I start the game, I get these weird black lines but that's ok. The real issue is with the messed up pixels on the text, and the incredible lag during in-game! It's really bad. Back when I used 0.9.8, the lines were there but performance wasn't this crappy. I even had low end hardware back then, using Ubuntu 11.10 I believe. I would have thought with an upgrade to my graphics hardware, it would be better. It certainly isn't.

I'm using the ZZ Ogl PG CG 0.3.0 plugin for GS. Whenever I try using GSdx 0.1.16, the game's won't even start. When I try to use ZZ Ogl PG CG 0.4.0, all I get is a white screen. I can hear the game playing in the background but nothing but a white screen.

When using ZZ Ogl 0.3.0, if I configure it to 16x AA and Interlace 0, the broken text pixels are fixed slightly. At least they're readable. What can I do to fix this? How can I make use of GSdx or ZZ 0.4.0?

**_Controller Plugin/Pad_**:
I only have TWO options for this. Either NULL or OnePAD 1.1.0. OnePAD 1.1.0 is fine with my keyboard and whatever I set it to. It however is not fine with my original PlayStation 2 Controller. It detects all my controller's keys during configuration, but in-game it behaves as if I have no controller. Nothing I hit gets detected. Back in 0.9.8, there used to be a lot more plugins for PAD. What happened to them? How can I try and get different plugins for the Linux version of PCSX2 1.0.0? I searched the website, and can only find Windows plugins or archived plugins.

My system specs:
CPU - AMD Phenom II 965 3.4GHz
GPU - Nvidia GeForce GTX 680 2GB
RAM - 8GB DDR3 1333MHz
OS - Ubuntu 12.10 64Bit

Any help or guidance is greatly appreciated!

---

### Post by myromance123 on 2013-03-25
Bump!

I managed to get GSdx to work. Any time I make a change to a plugin, I have to make sure it's being done on a fresh startup of PCSX2. GSdx is definitely a huge improvement in terms of graphical quality, but any time it comes to rendering something 3D it starts to massively lag. I thought that maybe my CPU wasn't up to par, but under CPU usage I'm only getting about 45-50% being used (and that's with a song playing, 50+ tabs open in FF, CrossOver 12.1 open). Why is PCSX2 emulating so slowly on my computer?

If I had a Sandy Bridge CPU or an Ivy Bridge CPU, would SSSE3 and SSE4.1 really make that much of a difference in terms of performance?

Note that I tried under Configurations, both OpenGL (software) and OpenGL(hardware)[experimental]. While software works, but sluggishly, hardware is unplayable. Case in example, when I tried Need For Speed Most Wanted BE, getting to the main menu is ok. Once in the main menu, everything is garbled up.

Games I've tried so far:
Kingdom Hearts 2
Burnout Revenge 4
Need For Speed Most Wanted BE

Any guidance is honestly greatly appreciated. If not on how to configure PCSX2, then maybe on good hardware tips. I'm thinking of getting a new CPU and mobo, but not in the nearest time.

P.S: I am using the 310.14 Nvidia drivers from the Ubuntu repositories. Would the 313 drivers offer a significant boost?

---

