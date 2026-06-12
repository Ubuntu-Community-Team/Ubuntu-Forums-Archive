---
title: "PCSX graphics options only OpenGL Driver after upgrade to 64 bit"
date: 2014-12-03
forum: Emulators
---

### Post by michael-piziak on 2014-12-03
I was running PCSX on 12.04 lts 32 bit and it gave me the option of choosing between OpenGL Driver or the VideoX cpu simulated graphics.

After upgrading to 12.04 lts 64 bit, PCSX only allows me to see the OpenGL screen when I click Configuration->graphics

The downside to this is that I can only get to about 1024 x 670 resolution in OpenGL and it won't work properly if I enter a higher resolution or select full screen.    Previously, when I didn't use OpenGL (in the 32 bit Ubuntu), it worked any resolution and full screen under VideoX

Comments or thoughts please - ?        
Do other users that are using 64 bit installs not get an option to choose between the two also ?

---

### Post by michael-piziak on 2014-12-05
Update:   I figured out the problem.  One has to go to "bios and plugins" to change PCSX from openGL to the VideoX option.   I was simply going to configuration->graphics, where openGL was already selected.

The upside to my experience is that I began running PCSX at 1280 x 800 in OpenGL and the graphics were better, and that resolution nearly fills up the screen.  I will keep PCSX on OpenGL.    For other emulators, OpenGL didn't work or looked fuzzy, but it works good for PCSX.

---

