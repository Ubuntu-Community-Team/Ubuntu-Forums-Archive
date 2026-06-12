---
title: "Font hinting broken"
date: 2019-07-09
forum: Desktop Environments
---

### Post by Kyentei on 2019-07-09
Hello all,

I cannot, for the life of me, seem to get font hinting to work. This is on a fairly fresh install of Ubuntu 19.04

screenshots, in which you can see nothing changes:
[ATTACH=CONFIG]283590[/ATTACH]
[ATTACH=CONFIG]283591[/ATTACH]

I've tried the following:

[LIST]
[*]Setting FREETYPE_PROPERTIES in /etc/environment 
[*]Symlinking 10-hinting-full.conf and 10-no-sub-pixel.conf in /etc/fonts/conf.d/ 
[/LIST]

I'm using an XPS 13 (HiDPI) with an external monitor. My laptop screen is disabled when the external monitor is attached. The problem only occurs on the external monitor (or I simply can't see it on a hidpi screen).

If anyone's got a clue on how to resolve this, I'm all ears.

**Edit:** Enabling Subpixel (for LCD screens) instead of Standard (greyscale) **and rebootin****g** seems to have made things a lot more usable!

---

