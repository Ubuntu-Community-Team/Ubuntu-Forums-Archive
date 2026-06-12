---
title: "steam - Weird lag problem on Killing Floor &amp; Counter Strike"
date: 2013-02-18
forum: Gaming &amp; Leisure
---

### Post by TheNoobyPro on 2013-02-18
Well I have an odd problem that seems to occur in Killing Floor and Counter Strike (these are the only games I can play on Linux, so I can't test it on any other games). The problem is, whenever I start a game/join a server, I get extremely bad lag, but before I start it, when I'm in the menu, etc... it runs fast and smooth. Now here's the weird part, once I leave the game/server and go back to the menu, it lags just as bad as it did in the game. I've fixed the problem on Counter Strike (non-source), but adding these launch parameters ```
-dxlevel 71 -no3d9ex -windowed
```, I'm not sure that the dx parameters work, because it didn't start working correctly until I started it in Windowed mode. I've tried these same parameters with Killing Floor, but it didn't work.

Does anyone know a solution to this problem or  have experienced it themselves?

Hardware:
Athlon 64 3800+
1.75GB DDR RAM
GeForce 7300 LE
Ubuntu 12.04 LTS 32-bit

---

### Post by r00st3r3 on 2013-02-19
This may be a dumb question but are you running the Linux version of Steam or are you running a version in Wine? Both of those games will run on Steam for Linux without any issues. I have played them both.

---

### Post by TheNoobyPro on 2013-02-19
> **r00st3r3 said:**
> This may be a dumb question but are you running the Linux version of Steam or are you running a version in Wine? Both of those games will run on Steam for Linux without any issues. I have played them both.


I've tried both the Wine and Linux version. Thinking it's a hardware compatibility issue.

---

### Post by ZarathustraDK on 2013-02-20
Don't know if it's related, but try running it in native resolution.

When I first installed Killing Floor it started up in 800x600 resolution. One would think that that would make it blazingly fast at an, albeit, decreased quality. I ran like cold molasses uphill, though. Changed the resolution to 1920x1080 and it ran like a dream.

Generally that seems to be the case with games under Unity for me. It's either native fullscreen res, or windowed lesser. Fullscreen decreased res is asking for problems.

---

