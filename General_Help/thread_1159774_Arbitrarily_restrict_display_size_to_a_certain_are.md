---
title: "Arbitrarily restrict display size to a certain area"
date: 2009-05-15
forum: General Help
---

### Post by Andreas1 on 2009-05-15
Here's the problem: My laptop screen has lost an area about the size and position of a windows sidebar to color patterns caused by a short-circuit since both hinges broke (don't buy Acer, by the way). So what i would need to do now to keep it usable is to restrict the display output to the remaining pixels. meaning that panels, maximized windows and other applications will be restricted to the area of the screen that still works. that would be the left 1200x1050 of 1400x1050, the lost area is at the right. is there a way to do this?

---

### Post by dcstar on 2009-05-15
> **Andreas1 said:**
> Here's the problem: My laptop screen has lost an area about the size and position of a windows sidebar to color patterns caused by a short-circuit since both hinges broke (don't buy Acer, by the way). So what i would need to do now to keep it usable is to restrict the display output to the remaining pixels. meaning that panels, maximized windows and other applications will be restricted to the area of the screen that still works. that would be the left 1200x1050 of 1400x1050, the lost area is at the right. is there a way to do this?

Possibly, if you create a Virtual Resolution in the xorg.conf file - but I really doubt it.

The easiest way may be to set up Virtual Machine that you run in the usable screen area.

---

### Post by Andreas1 on 2009-05-15
> **dcstar said:**
> Possibly, if you create a Virtual Resolution in the xorg.conf file - but I really doubt it.

The easiest way may be to set up Virtual Machine that you run in the usable screen area.

I tried the Virtual Resolution in xorg.conf, tried 1200x1050, but it falls back to 1152x864 (which is next possible 4:3 resolution), stretched.

Virtual Machine is not an option, my computer runs with 800mhz.

Is there any Window Manager that would allow to be fooled like that maybe?

So far i created a gnome panel that is 200px wide at the right, this keeps maximized windows at the right place, but the top and bottom panel are still stretched beyond because the vertical panel is between them rather than vice versa, and anything fullscreen is also beyond.

---

