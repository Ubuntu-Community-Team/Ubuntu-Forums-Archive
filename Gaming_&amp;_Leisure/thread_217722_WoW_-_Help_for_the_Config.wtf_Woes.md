---
title: "WoW - Help for the Config.wtf Woes"
date: 2006-07-17
forum: Gaming &amp; Leisure
---

### Post by nalthien on 2006-07-17
I decided to do some research deeper into World of Warcraft performance under the patched version of WINE.  One of the issues I have is that I *need* to run the game at 1600x1200 resolution -- I have an LCD monitor and its native res. is 1600x1200.  Anything less is quite blurred.

That said, I'm only running on an ATI Radeon 9800 PRO--enough to push 1600x1200 with a good number of settings turned down under windows and, I'm not surprised, more turned down under Linux.  But, there are the bugs--I can't load the d3d version at all (it doesn't even start up) to change my graphics settings, so I have to do it all by hand via the Config.wtf file.

However, there are some changes that, when made, cause the infamous "mouse bug" to show up (the bug that the patch is meant to resolve).  

If I set any of the following in the Config.wtf file, the mouse acts as it does without the patch.

```
SET TerrainMip "1" /* Sets "Terrain Detail" setting to low
SET frillDensity "8" /* Any setting here causes bug */
SET ffx "0" /* Turns all glow effects off.
SET ffxGlow "0" /* Turns off fullscreen glow effect */
SET weatherDensity "1" /* Any setting here causes bug */
SET spellEffectDetail "1" /* Any setting here causes bug */
```

*C-style comments added by me for description--they do not exist in my Config.wtf file.

I'd really like to be able to turn the terrain detail down to low, that's the big one that will gain me a few extra FPS.  Anyone know of a workaround?

---

