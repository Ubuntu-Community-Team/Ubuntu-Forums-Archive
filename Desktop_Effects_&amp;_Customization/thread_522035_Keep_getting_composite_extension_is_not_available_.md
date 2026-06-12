---
title: "Keep getting composite extension is not available error"
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by effec on 2007-08-10
I followed the sticky on installing my mobile radeon x300 exactly.

Now under restricted drivers, ATI accelerated graphics drive is marked in use, but not "checked" as enabled. 

I did the flgrx info thing in terminal and my card came up, no mesa error etc.

[B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300
OpenGL version string: 2.0.6334 (8.34.8 )
[/B]



Is there some other reason why my desktop effects wont work?



EDIT 1: After doing a full restart now i get the mesa problem. Xlib:  extension "XFree86-DRI" missing on display ":0.0".

[B]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/B]

Why would this happen when before, i already had the ati screen?

Am i supposed to be using the restricted drivers that are automatically enabled on a clean install or am i supposed to fix that in someway?


EDIT 2:
 
I downloaded and used envy to get me the right driver. Under restricted driver manager, i now see the ati drivers enabled and in use....is this supposed to be the case? I tried to start up desktop effects once more but i still get the same error for no composite extension.

---

### Post by SkippyIsForYou on 2007-08-10
[https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28composite%29%7C%28X%29](https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28composite%29%7C%28X%29)

Install your X Composite manager.

---

