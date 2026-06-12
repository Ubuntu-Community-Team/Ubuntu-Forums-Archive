---
title: "Visual Effects Crashes Ubuntu"
date: 2007-11-23
forum: Desktop Environments
---

### Post by moliver on 2007-11-23
I've used Linux for all of about 2 hours now, so talk very slowly..

I managed to install the proprietary nVidia drivers for my GeForce 6600, but whenever I go into the 'visual effects' options if I click on anything other than none (including custom, which I got by running some craziness I saw in another post) my computer crashes and boots me back to the log in screen. (Makes me very happy for Firefox's 'restore session')

Please help :(

---

### Post by Linteg on 2007-11-23
Is 3D-acceleration working with other programs? (try running glxgears for example)
Compiz-Fusion (which is the window manager that does all the pretty stuff) is still under heavy development and could be a bit unstable on some configuration, you might be unlucky there, but on the other hand the gf6600 and nvidias proprietary drivers should be stable.
You could also try removing whatever software that made "custom" available (i presume it's compizconfig-settings-manager, ccsm).

---

