---
title: "Forcing Xorg to use a VESA driver?"
date: 2009-04-10
forum: General Help
---

### Post by jsbiff on 2009-04-10
First, my apologies if this isn't the best forum to post this in - I'm not sure which of the forums this would best be filed under.

   My laptop has an nVidia video card, BUT it's basically fried. I'm waiting for replacement hardware from Dell (which has been delayed rather long). In the meantime, I'd like to try to get into Ubunut so that, if nothing else, I can burn my home directory to a DVD.

   The problem is, Xorg is, I believe, detecting my nVidia card, and attempting to load the Xorg nv driver, at the highest resolution that the card supports. Unfortunately, because the card is basically fried, the whole computer locks up when it tries to do this, and the screen becomes all crazy.

   Under Windows, I'm able to boot the computer if I first go into Windows Safe mode, then into device manager, and force Windows to uninstall the nVidia driver. Then, the next time I boot into Windows, it will use a generic driver (I assume using VESA video modes).

   Is there a way to do something similar in Ubuntu - to force Xorg to use a generic VESA driver with 1280x1024x32? That is what Windows is running at, and that seems to be working.

   I'd really like to be able to get into Ubuntu while I'm waiting for my new hardware from Dell.

---

