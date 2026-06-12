---
title: "Light grays display as white."
date: 2006-10-05
forum: Desktop Environments
---

### Post by Bastanteroma on 2006-10-05
When I installed Dapper on a friend's computer yesterday I realized that the same gtk theme displays differently on his computer.  

Attached is a screenshot from his computer.  

On his computer, in use and in the screenshot, I can see a divider in Nautilus between the tree on the left and the main pane.  

On my computer the toolbars and that divider are the same white as the background.  

In Nautilus all I can see, in use or in that same screenshot, is the handle separating the tree from the main pane.

His computer has an old nvidia TNT2 card using the nv driver.

I have an intel 910 using whatever driver is default (810?), which happens to have a bug related to video contrast in Totem, for what that's worth.

Any ideas?

Can everyone else see the divider in their Nautilus, or in that screenshot?

---

### Post by CatKiller on 2006-10-05
I can see the divider in that screenshot. Monitor brightness? Gamma setting? Who knows.

---

### Post by Bastanteroma on 2006-10-06
Both computers use the same Dell model lcd and I even swapped them, so I think the monitor can be ruled out.  I played with the gamma settings too, and that's not it - no matter how dark I make my computer I don't see the divider and no matter how light I make the other I see the divider, until I can't see much at all.

---

### Post by CatKiller on 2006-10-06
I haven't used an LCD screen, so I don't really know how the brightness and contrast controls work on those.

There is a set of utilities called xgamma that let you set the gamma correction of X, and standard images on the Internet for calibration. Have a google for colour correction if you're interested.

---

### Post by Bastanteroma on 2006-10-06
I tried xgamma and it isn't a gamma problem - no matter how low the value I set, I don't see the divider in Nautilus.  I also tried changing to the vesa driver, hoping for a magical solution.

---

### Post by CatKiller on 2006-10-06
Some graphics cards do just have crap colour and contrast. It's not as extreme as your seems to be, but ome of my video cards comes out very dark for fullscreen things. Have you googled for your make/model of graphics cards to see if others have had the same problem, and if they managed to fix it?

Also, the NVidia driver that I've installed lets me adjust Brightness, Contrast and Gamma. Does the driver that you're using?

To clarify - I'm using the NVidia proprietary driver, and I've installed something called nvidia-settings that lets me fiddle with these things. I don't know if other drivers have something similar, because I haven't used them.

---

### Post by Bastanteroma on 2006-11-27
Reinstalled windows to sell the computer and the display is too light there, so it's a hardware problem, shared with another intel integrated computer I use.

---

