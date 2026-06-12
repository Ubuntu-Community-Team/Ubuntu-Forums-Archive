---
title: "Twinview - monitor on VGA is flickering"
date: 2010-11-11
forum: Desktop Environments
---

### Post by _sokre_ on 2010-11-11
Hi all,

Recently i've installed 10.10 and have a problem with flickering screen on VGA. I have 64-bit release, ge force 210, nvidia propietary drivers and two monitors:
- AOC_1920*1080_60_DVI
- Philips_1280*1024_75_VGA
- nvidia-current, 260.19.12, 2.6.35-22-generic, x86_64: installed
No matter which monitor is attached to VGA, it flickers randomly every couple of minutes. Sometimes it flickers when i use mouse or keyboard, but sometimes it flickers by itself.

Possible solutions? Thx.

---

### Post by _sokre_ on 2010-11-15
anyone? thx.

---

### Post by _sokre_ on 2010-11-15
[http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)

Instead of setting those options, i've set "Prefered mode" in PowerMizer to "Prefer Maximum Performance" and now there is no more flickering.

---

### Post by _sokre_ on 2011-01-04
> **_sokre_ said:**
> [http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)

Instead of setting those options, i've set "Prefered mode" in PowerMizer to "Prefer Maximum Performance" and now there is no more flickering.

Unfortunately, above didn't permanently workaround it, it was just less frequently...

Found another workaround, and now for about 1 hour monitor didn't flicker:

src: [http://www.piotrkrzyzek.com/nvidia-powermizer-power-levels-temporary-workaround/](http://www.piotrkrzyzek.com/nvidia-powermizer-power-levels-temporary-workaround/)

**One of the best changes you can do (or so the site says) is this:**
[INDENT]**nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1**
[/INDENT]**You  will have to do that at every boot. So, easiest solution is to just  stick that into a script and have it run at every boot (or login). For  me, I put it into “nvfixes.sh” into my “~/.kde/Autostart/” folder. Here  is my whole script:**
[INDENT][B]#!/bin/bash
 nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1[/B]

[/INDENT]

---

