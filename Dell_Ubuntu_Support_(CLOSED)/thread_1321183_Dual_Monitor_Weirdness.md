---
title: "Dual Monitor Weirdness"
date: 2009-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by manekineko2 on 2009-11-09
I'm trying to use dual monitors on my Dell Latitude E6500.

My video card is an Intel GMA 4500.
Laptop screen is 1920x1200.
External screen is 1920x1080 connected via a DisplayPort adapter to HDMI.

Everything works perfectly under Windows.

When enabling via Preferences > Display it's creating a weird effect where the desktop (the area that has a background and where I can put icons and right click to get normal desktop options) becomes a tiny box.  Everything else is colored in a solid color, where I can move the mouse pointer without problems, and where I can drag applications but they leave behind ghosts everywhere they go.

I've tried various things that resulted in the desktop area getting larger (but still not large enough), or the primary display getting moved onto my external, or the displays getting mirrored (at a really low resolution).

Looking at xorg.conf, the virtual display is properly set at 3840x1200.

Has anyone ever seen this before and have any ideas on how to fix this?

---

