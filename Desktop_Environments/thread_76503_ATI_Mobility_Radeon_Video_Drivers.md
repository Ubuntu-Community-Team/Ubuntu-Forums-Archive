---
title: "ATI Mobility Radeon Video Drivers"
date: 2005-10-15
forum: Desktop Environments
---

### Post by dwessell on 2005-10-15
Hey all..

I have a Compaq Presario 2100 Notebook, with ATI Radeon Mobility videocard. I've noticed that when scrolling through pages, the pages tend to jump... In Windows, I would associate this with generic video drivers, and install specific ones.. Is it the same case in Ubuntu?

Would I install drivers from ATI's site, or some specific to Ubuntu? A point in the right direction would be much appreciated.

Thanks
David

---

### Post by mikeh on 2006-02-16
[QUOTE=dwessell]Hey all..

I have a Compaq Presario 2100 Notebook, with ATI Radeon Mobility videocard. I've noticed that when scrolling through pages, the pages tend to jump... In Windows, I would associate this with generic video drivers, and install specific ones.. Is it the same case in Ubuntu?

Would I install drivers from ATI's site, or some specific to Ubuntu? A point in the right direction would be much appreciated.

Thanks
David[/QUOTE]
David,
the drivers from ATI do not support this chip, so use the ati/radeon driver that comes with Ubuntu. Its just standard xorg, not ubuntu-specific.
The "jumping" might be from the use of anti-aliased fonts without hardware support.  Try turning off anti-aliasing, aka smoothing, in the font preferences.
  Is it still a problem?

---

