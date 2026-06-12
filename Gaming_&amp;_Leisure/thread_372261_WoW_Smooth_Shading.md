---
title: "WoW Smooth Shading"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by russianbandit on 2007-02-28
My WoW works great on my Feisty install. However, I did notice that it appears a bit jaggy on the screeen. I don't see this problem on my WinXP install. I tried to check the "Smooth Shading" option in my Video Settings, however, WoW crashes each time I try to do that. In fact it seems to crash everytime I mess with something in Video Settings. Therefore, I wanted to set "Smooth Shading" from withing Config.wtf file, but don't know the format for it. Anyone know what string will set the smooth shading on? Maybe my problem is something else. Thoughts?

---

### Post by Ferrat on 2007-02-28
the the wine appdb for WoW I think there is a list for all config.wtf options :)

---

### Post by russianbandit on 2007-02-28
Any idea what these settings do?
Generally what's the M2 prefix mean?

SET M2UseClipPlanes = "1"
SET M2UsePixelShaders = "0"
SET M2UseShaders = "1"
SET M2UseThreads = "1"
SET M2UseZFill = "1"

---

### Post by Sammi on 2007-02-28
It is a known issue that WoW crashes if you change video setting while in opengl mode. The trick is to run the games in directx mode just so that you can change the settings you want and then run it in opengl again as usual.

The troubleshooting section of the community WoW/Wine howto explains this: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

