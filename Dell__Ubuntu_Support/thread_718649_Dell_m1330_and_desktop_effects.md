---
title: "Dell m1330 and desktop effects"
date: 2008-03-08
forum: Dell  Ubuntu Support
---

### Post by TonyLB on 2008-03-08
I've just installed ubuntu on my new Dell, with the intel graphics chipset.  Whenever I try to enable any desktop effects, through preferences/appearance/visual effects, I just get 'desktop effects could not be enabled', whatever level from normal up that I choose.

Is it the graphics card not supporting things, or something else?  What do I do now - I want to show unbelievers that we can beat aero.

Tony

---

### Post by pormogo on 2008-03-08
Using the Intel GMA3100 (I think that's the 965 based graphics accelerators name) will cause compiz to return an error about the module being blacklisted. This is due to some video playback features not being correctly supported. There is workaround for this issue at the url below but it does break video playback until you tell gstreamer-properties (for gstreamer based players) to direct video through X11 (no XV). Or go into the individual player to make the adjustments. 

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

---

