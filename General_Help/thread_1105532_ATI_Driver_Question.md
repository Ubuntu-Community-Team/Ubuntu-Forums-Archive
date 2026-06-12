---
title: "ATI Driver Question"
date: 2009-03-24
forum: General Help
---

### Post by ashlanky on 2009-03-24
I just installed Ubuntu 8.10 and all my drivers are good except the graphics driver. The Hardware Drivers window pops up and asks to activate my ati driver and I click activate and an error pops up saying "System Error: E:Unable to correct problems, you have held broken packages." Any idea how to fix this? I am fairly new at linux and have no idea what this means. And my Graphics card is a ATI Radeon 4870 if that makes any difference.

---

### Post by mb_webguy on 2009-03-24
Try opening Synaptic Package Manager and selecting Edit->Fix Broken Packages.  You could also click the Custom Filters button and the Broken category to see exactly which packages are causing the problem.  While you have Synaptic open, click Reload, Mark All Upgrades, and Apply.  

Once that's done, exit and try installing your video card driver again.

---

### Post by ashlanky on 2009-03-24
It's still is giving me the same error.

---

### Post by zvacet on 2009-03-25
System>admin>software sources and in first tab check all except **sources**, and under updates check first two (you don´t need backports and proposed repos).Refresh and try to install again.

---

