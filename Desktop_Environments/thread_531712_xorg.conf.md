---
title: "xorg.conf"
date: 2007-08-21
forum: Desktop Environments
---

### Post by barbro on 2007-08-21
Since feisty (xorg 7.2) its possible to run the x-server without xorg.conf!
Now i try to remove my xorg.conf and restart gdm... works fine except that how do i now load my binary drivers like nvidia or synaptics(touchpad).

Do i have to use a minimal xorg.conf or is there any way to load the drivers on the fly (or is it expected in xorg 7.3+)

---

### Post by FuturePilot on 2007-08-21
I think it would be best to keep your xorg.conf.
The reason it works without it is so that if you mess up with the graphics drivers you can at least be in a graphical environment. (A step towards a bullet proof X) It's not really meant to be run without that config file though.

---

### Post by kerry_s on 2007-08-21
> **barbro said:**
> Since feisty (xorg 7.2) its possible to run the x-server without xorg.conf!
Now i try to remove my xorg.conf and restart gdm... works fine except that how do i now load my binary drivers like nvidia or synaptics(touchpad).

Do i have to use a minimal xorg.conf or is there any way to load the drivers on the fly (or is it expected in xorg 7.3+)

yes, you can run it without xorg.conf, but you need it to change the settings, it's kinda more like a settings file. got to love the new bullet proof X.

---

