---
title: "Upgraded Xorg and Intel drivers, kwin compositor now gives me the finger."
date: 2010-03-08
forum: Desktop Environments
---

### Post by immerohnegott on 2010-03-08
Seriously, that thing is not happy. Being that I have an Intel IGP on my laptop, and that Intel's drivers seem to be rather consistently getting less horrible, I opted to jump the gun and add the xorg-edgers ppa and update my graphics stack. The good news: things seem to be a little snappier. The bad news: KWin is now being a wanker.

 Compiz works (splendidly) with Emerald under LXDE (the only other DE i have installed right now), so compositing itself is working at the X11 level. Ran kwin --replace in terminal to get output, and when I load up system settings to enable desktop effects with OpenGL, it gives me a couple errors about GLX 1.3 functions and then shuffles off this digital coil:
```

WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
kwin(3780): Compositing self-check failed, disabling compositing. 
kwin(3780): Failed to initialize compositing, compositing disabled
```

On a hunch, I tried using dpkg to reconfigure Kwin, but that didn't do me any good. Oddly, the XRender mode works, but not for all effects.

Using an x4500MHD, by the way.

---

