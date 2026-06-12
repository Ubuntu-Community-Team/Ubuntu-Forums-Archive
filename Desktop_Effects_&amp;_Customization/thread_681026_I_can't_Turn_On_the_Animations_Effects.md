---
title: "I can't Turn On the Animations Effects"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by juancarlos1984mg on 2008-01-28
Hi everyone, my problem is that I can't Turn On the Animations Effects (I want to activate the effect that burn up the window when it close by example).

When I do click on the checkbox of "Animations" and enter to the "Animations" configuration, I can see that the selection disappears, then I do click again in the checkbox to enable the effects and click in "Close" button. When I'm in the Manager, the selection disappears again. Anyone have a solution or know something about my problem. Is the same problem with others effects that I don't remember right now.

Thanks.

By the way, I'm using a Desktop with the next specs:

Operating System: Ubuntu 7.10 Gusty Gibbon AMD64
Processor: AMD64 Athlon 3200+
RAM: 1.28 Gb
Graphics Video Card: ATI Radeon Xpress 200 of 128 Mb

---

### Post by Afkpuz on 2008-03-11
Have you gotten other effects to work?  I'm wondering if you have your system set up correctly.  

Have you installed your video drivers?

Installed xserver-xgl?  You need this because you have an ATI card

Have you enabled desktop effects?

---

### Post by pidgeon on 2008-03-12
i'm having the same problem. i have my effects turned on, but, the animations won't stay turned on.

---

### Post by Zorael on 2008-03-12
If you're using the CompizConfig Settings Manager (or ccsm; package name **compizconfig-settings-manager**), you may want to convert to flat-file configuration backend, in Properties. Make sure to Export your settings first, then change to flat-file, then Import.

This fixed some plugins not staying active for me.

---

### Post by pidgeon on 2008-03-12
how do you do the exporting and importing?

---

### Post by pidgeon on 2008-03-12
i did all that and it's still not working. and, btw, i'm running 7.10 with an nvidia video card.

---

### Post by Zorael on 2008-03-12
Export, Import and Configuration Backends can be set in Preferences, in the Compiz-Fusion Settings Manager mentioned earlier.

---

### Post by pidgeon on 2008-03-12
yeah, i did all that, and, it's still not working.

---

### Post by osx on 2008-04-12
Any resolution to this yet. I'm having the same problem.

---

