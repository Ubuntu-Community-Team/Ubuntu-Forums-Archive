---
title: "Broken window text rendering"
date: 2015-05-15
forum: Desktop Environments
---

### Post by rickard.westerlund on 2015-05-15
I am using Ubuntu 14.04 and have this strange issue that happens randomly. If I have a few windows open and switch between one it can occasionally completely mess up the text rendering for all other windows. If this happens I can't do a whole lot more than restarting the computer because it's almost impossible to make anything out anymore (screenshot).
It does not appear to affect some areas with text rendering, like the unity launcher which looks fine.

I really don't know what could be wrong, I've tried reverting any changes I might've done so I'm using the default theme and fonts but the issue is still there.

---

### Post by ajgreeny on 2015-05-15
This looks like a graphic card or driver problem; what hardware do you have and which driver are you using for it?

Alternatively it might be text rendering settings, ie, anti-aliasing, hinting and sub-pixel ordering, though I don't know how you can change that in unity as I don't like it, nor use it.

---

### Post by rickard.westerlund on 2015-05-15
I have an Nvidia 660 GTX and driver appears to be Gallium 0.4 (full glxinfo output attached). To add, Google Chrome does not get affected by the rendering issues either. It seems that only the Gnome windows and desktop are affected.

EDIT: I've updated to the latest drivers, from 340 to 346. Now it says Nvidia instead of nouveau/Gallium 0.4. I'll test a bit and see if the issue is still there.

EDIT2: I haven't had any more issues so I suppose this is resolved. Thanks!

---

