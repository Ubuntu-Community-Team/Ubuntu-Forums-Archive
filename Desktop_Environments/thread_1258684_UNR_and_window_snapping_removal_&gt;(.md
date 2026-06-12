---
title: "UNR and window snapping removal &gt;:("
date: 2009-09-05
forum: Desktop Environments
---

### Post by pwithem on 2009-09-05
SETUP.  I just installed UNR 9.04 on my new 1005HA EEE PC.  Not a fan of the default desktop view, but I like the attempt to maximize desktop real estate and reduce processor overhead.  

PROBLEM.  My main gripe is trying to turn off window snapping.  A window snaps to other windows, top, bottom, and side edges of the screen.  I cannot describe how infuriating this is, but it amounts to a constant tug of war to get anything done on this small screen.  

SOLUTION.  The only solutions I've encountered involve enabling compiz desktop effects and configuring with ccsm.  Ignoring for a moment that this goes against the lean concept of UNR, I've identified in the Window Management category that "Snapping Windows" and "Move Window" are crucial to this cause.  I disable snapping windows entirely, disabling "constrain y" in move window, and enabling "lazy positioning" (not sure what it does exactly) in move window.  Also, I've disabled as much effects, animations, etc. to make as close as possible to normal UNR behavior.

RESULTS.  
(1) Using the compiz effects gives me exactly the window handling behavior I want - gone is the claustrophobic confinement of the default UNR environment.  
(2) However, I've defeated the purpose (I think) of even using UNR if I'm enabling compiz - the window decorations effect seems to override Maximus and I would expect that the battery life will take a hit.  It seems that with compiz enabled, different drivers/libraries are being brought to bear that presumably use more cpu.  
(3) If I try to be sneaky and setup everything in compiz, then disable desktop effects entirely in the hopes that some global variables are now set where I want them...well that doesn't work.  It just goes back to hardcore snapping.    

QUESTION/PROBLEM
Does default UNR have a config file somewhere to disable snapping or reduce the snapping range to 0?  I remember in the past using KDE I could reduce the range in some setting down to 0, effectively disabling snapping.  

Thanks for you help.  -Pat

---

### Post by pwithem on 2009-09-10
So, no one knows how to disable or even control window snapping without using compiz?

---

