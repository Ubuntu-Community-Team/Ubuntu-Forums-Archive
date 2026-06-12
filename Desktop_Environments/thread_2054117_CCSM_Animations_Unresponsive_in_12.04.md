---
title: "CCSM Animations Unresponsive in 12.04"
date: 2012-09-06
forum: Desktop Environments
---

### Post by aPaonessa on 2012-09-06
After upgrading from 11.10 via terminal, I began configuring my desktop environment and found that any changes made in CCSM had no affect on the desktop environment.

I'm using a gnome shell but any changes I make to animation settings in CCSM don't change the way my windows behave. 

I've removed ccsm and later re-installed it (sudo apt-get remove ... ) and removed unity.

Any ideas?

Thanks,
Anthony

---

### Post by Frogs Hair on 2012-09-06
The GNOME Shell uses Mutter, a compositing window manager based on the Metacity window manager, and the Clutter toolkit to provide visual effects and hardware acceleration. That is why Compiz won't work.

---

### Post by aPaonessa on 2012-09-06
> **Frogs Hair said:**
> The GNOME Shell uses Mutter, a compositing window manager based on the Metacity window manager, and the Clutter toolkit to provide visual effects and hardware acceleration. That is why Compiz won't work.

Oh, got it! Thanks for the help. Unity 3D has been giving me problems so I guess I'l play the nVidia driver game until I can get it to work. Does the Clutter toolkit offer features similar to Compiz?

Thanks,
Anthony

---

### Post by zombifier25 on 2012-09-07
Nope, but more and more features are being ported.

---

