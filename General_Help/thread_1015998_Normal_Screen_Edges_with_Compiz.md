---
title: "Normal Screen Edges with Compiz"
date: 2008-12-19
forum: General Help
---

### Post by aslamp on 2008-12-19
One thing I've noticed with Compiz enabled is that when you try to click at the top of the screen, say, to select a window from the window list, Compiz grabs the click and doesn't pass it through to gnome. 

The same thing with the volume icon I have in the corner.

As far as efficiency goes, it takes a relatively long amount of time to go to the edge, then back away from it until Compiz doesn't see it as an edge action. 

Is there anyway to bypass this in order to use the screen edges effectively?

I would still like to keep my current screen actions (Desktop Wall, etc.) activated, if possible.

Thanks.

---

### Post by aslamp on 2008-12-20
bump?

---

### Post by germclown on 2009-04-23
Same problem here. Got a 2 pixel border around the screen that is unclickable for anything but Compiz stuff. Can't even grab windows or scrollbars unless I click >2px from the edge. :confused:

I've had the problem before (unsolved) but didn't see it while using Ibex. But it came back with today's Jaunty install. I'll mess with CCSM a bit and post any successes.

update: seems a 2x2px square in each corner is still clickable (can click the Applications menu from the very corner, for example).

---

### Post by germclown on 2009-04-23
Did some browsing on the Compiz boards. Mine was an edge flipping problem. Apparently some combinations of Desktop Wall/Cube, Edge Flip DnD/Pointer/Move will cause those pixels to refuse normal actions to make the chosen options usable.

I was using Desktop Wall, Expo, Edge Flip DnD, Edge Flip Move and had the 2px problem. I disabled Edge Flip DnD and I got my edge clicking back.

---

