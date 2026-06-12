---
title: "IBM T42, external DVI screen sized as LVDS, too small"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Mikebat on 2009-02-10
I have a IBM T42 with Radeon Mobility 7500, and Xubuntu 8.04.  It has a 1024x768 LVDS screen, and a 1280x1024 external LCD panel connected to the DVI port on the docking base.  At work, it is docked and I use the external screen exclusively.  At home, I seldom need to use my notebook from work, but when I do, its at 1024x768 using the notebook screen alone.

Connected to the external LCD, when X loads, the GDM login screen is sized and centered in a 1024x768 screen within the 1280x1024 LCD screen, the upper left corner of which coincides with the upper left corner of the 1280x1024 LCD screen.  When I login to the Xubuntu desktop, the panels are also sized to the 1024x768 internal LVDS screen that I am not using.  New windows also launch inside this area, but after they are launched I can stretch them to fill the 1280x1024 screen.  

I was able to get the panels to stretch across the 1280 width of the external LCD screen by adding "Virtual 1280 1024" to my Screen definition.  But new windows still launched inside the 1024x768 screen-within-a-screen.  I used xrandr to turn off the LVDS, and new windows now appear as expected, not limited to an invisible 1025x768 virtual screen.

I would like to figure out how to set things up so that when it's docked and the 1280x1024 screen is attached, that's the screen size it uses and places windows accordingly.  When it's not docked and has only the LVDS, is uses that screen and places windows accordingly.  I can run xrandr after logging in, but that only affects the current session. I'd like this to happen automatically.  I guess what I want to do is clone the LVDS display to the DVI-0 display when it's present, but use the 1280 resolution; and use the LVDS at 1024x768 when the DVI-0 is not connected.

Can someone point me in the right direction?

---

### Post by Mikebat on 2009-02-17
Bumpity bump-bump.

---

