---
title: "redirected direct rendering yet no direct rendering?"
date: 2009-03-30
forum: Desktop Environments
---

### Post by Locutus_of_Borg on 2009-03-30
I am using DRI2 and all the latest xorg, mesa, drm/dri2 stuff from git with the latest intel driver also from git.

I have working redirected direct rendering via dri2, 3-d applications are smooth and running fine, 1000+ fps in glxgears, but glxinfo tells me I do not have direct rendering.  Xorg.0.log tells me i have direct rendering from DRI2.  

Is there some way to make applications think I am running the old direct rendering from the DRI infrastructure?

I ask this since xbmc will not run without direct rendering enabled and does not recognize DRI2 as providing direct rendering.

Downgrading to ancient xorg 1.5 is not really viable.

---

### Post by Locutus_of_Borg on 2009-03-31
For the sake of posterity, I got xbmc to start by editing the following two files:

/xbmc/linuxport/XBMC/tools/Linux/FEH.py 
/xbmc/linuxport/XBMC/tools/Linux/.svn/text-base

located in the source of XBMC, and removing the lines that check for directRendering towards the end of each file, then recompiling.  Now it starts up fine.

glxinfo still says no direct rendering, but so far all my other applications are working with DRI2

---

