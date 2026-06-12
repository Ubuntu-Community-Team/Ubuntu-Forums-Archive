---
title: "World of Warcraft, wine, ATI radeon 1100 crash"
date: 2006-11-30
forum: Gaming &amp; Leisure
---

### Post by pie-rate on 2006-11-30
Alright, here's what I've done so far:
Got wine 0.9.26
Got some DLLs linked to from the wine appdb page for world of warcraft and put them in ~/.wine/windows/system32
Copied a working WoW install off my gaming box
Deleted Interface, WDB, and WTF/Accounts
Changed Config.wtf so that it had lines to improve sound quality and use opengl instead of direct x

When I start WoW ("wine WoW" from the WoW directory), it crashes almost immediately with an ACCESS_VIOLATION exception.

When I start WoW with d3d ("wine WoW -d3d" from the WoW directory), it doesn't crash but the 3d graphics kind of start halfway down the screen.

How do I fix the access_violation error?

---

### Post by pie-rate on 2006-11-30
Never mind, I fixed it by turning off full screen glow effect. Now it freezes after entering the game world.

---

### Post by hikaricore on 2006-11-30
People have had this issue before and it was traced oddly enough to the minimap.  There's a mod that disables it in building and on zone in.  You may want to search around curse-gaming or ui.worldofwar.net for it.  It's specially made to sidestep the issues of running in linux.  Also make sure you're using 24bit color depth, I had issues with opengl crashing or doing weird things like howing models inside out before I corrected this.

Not saying this is your surefire solution but it could be a possible fix.

---

