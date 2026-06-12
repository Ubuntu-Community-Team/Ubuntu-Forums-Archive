---
title: "fglrx xscreensaver #@^%!!!"
date: 2005-11-18
forum: Desktop Environments
---

### Post by zwalkert on 2005-11-18
I'm running an ATI X300 chipset with a dual monitor setup  under Breezy.  After quite a lot of frustration I have managed to get 3d acceleration working.  The reason I did this was to improve performance of xscreensaver with 3d routines.  They were working before, just not really well.  Now that I have 3d accell working (fgl_glxgears runs fine), xscreensaver will not display any routines that use 3d acceleration!  Well, I stand corrected - if I set GetViewPortIsFullOfLies to "False" in my .xscreensaver file, xscreensaver will run them but only on one screen.  When I set it back to "True", regular screensavers work on both screens but the 3d offerings cause both monitors to just go blank.   I'm pulling my hair out here!

---

