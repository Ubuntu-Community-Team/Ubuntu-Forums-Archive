---
title: "Multisampling in World of Warcraft?"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by Jdurr1128 on 2007-01-14
I finished installing WoW with Wine this morning using ubuntu 6.10. Everything so far seems to be working equal to or better than how it ran in windows with one small exception: Multisampling. The only options I get with multisampling are 1x. I tried increasing the multisampling in the config.wtf file, but when the game starts it reverts back to 1x.

Ive spent quite a while looking for some information on how to increase the multisampling but I can't seem to find it anywhere. Has anyone had any luck with this?

---

### Post by kcakalinuxnub on 2007-01-14
I have a similar problem, when I change the ColorsBits from 24x24 to 24x16 or 16x16 it just reverts back to 24x24.When trying to run under d3d mode to change the settings it crashes.  In the Wtf config file if I change it manually it jsut reverts back to the same way.

---

### Post by hikaricore on 2007-01-15
This has been an issue with WoW for a long time, it almost always tries to set gfx level to max bit depth and 1x multisampling on startup.  The only way I ever found around this was setting it in windowed mode + maximized.  But I'm not sure if this still works and may still cause it to revert back. >.<  It also does this in windows on almost every system I've messed with it on.

Good luck.

---

