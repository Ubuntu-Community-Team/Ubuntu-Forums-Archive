---
title: "Tearing even with v-sync enabled (Radeon HD 5850)"
date: 2010-01-17
forum: Gaming &amp; Leisure
---

### Post by mazz0 on 2010-01-17
I recently got a Radeon HD 5850 and have installed the latest drivers from AMD in both Ubuntu Karmic and Windows Vista (both x64).

The problem is on both OSes I'm getting horrible tearing on fast moving video and in games and Compiz (games only in Windows, Compiz only in Ubuntu, obviously).

I've enabled v-sync and the display is set to 60hz in CC.  CCC advises that my TV supports 70hz, but there's no option to set that in CCC.  Is that relevant?  I'm connected to a 40 inch LCD via DVI->HDMI.

Any advice, anyone?

---

### Post by Settwi on 2010-01-17
Does it only tear in video games?  Because, it might be possible to set your max frame rate to like 60 fps, i don't know.  Possibly get an older driver from your manufacturer's website, that might be a problem, too.

---

### Post by mazz0 on 2010-01-17
Well, in Ubuntu there's tearing in Compiz and video playback, but I never expect the linux drivers to be very good.

In Vista I've only tried games, but it's most obvious in the pre-rendered videos at the start of games.

---

### Post by DarthScape on 2010-01-18
Partial solution to your linux tearing problem:

System > Preferences > CompizConfig Settings Manager > General Options > Display Settings

Uncheck "Detect Refresh Rate", Set refresh rate manually. Check Sync to VBlank.

Fixed about 90% of the tearing in compiz and video playback.

Just found that out the other day. I have a 9800gtx+... so doesn't seem like it should be tearing either; plenty of power there.

Hope that helps.

---

