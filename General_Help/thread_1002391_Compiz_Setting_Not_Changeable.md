---
title: "Compiz Setting Not Changeable"
date: 2008-12-04
forum: General Help
---

### Post by sdlynx on 2008-12-04
Every time I try to edit the settings for Compiz in CCSM it will not change it.  I can check something to enable it and when I close and open it the same old settings as before are still there.  I know Compiz is working because Negative is enabled already and the keys and effect do work for that.  What must I do to change my settings now?

---

### Post by collinp on 2008-12-04
Do you have the package "compizconfig-backend-gconf" installed? That is the package that the Compiz Config Settings Manager uses to store its settings.

---

### Post by eternalnewbee on 2008-12-04
Try changing your Visual Effects to Extra.
To do this, go to: **Main Menu> System > Preferences > Appearance > Visual Effects** tab.

---

### Post by sistarbliss on 2008-12-05
Sometimes that happens to me...have you installed compiz fusion icon?  If you have that installed and loaded you can try to reload window manager that way.  I have to do that for emerald themes.  Seems like I have to do it every now and then for the compiz preferences.

---

### Post by eternalnewbee on 2008-12-05
> I have to do that for emerald themes
If you want emerald to be your default themes manager, press **ALT-F2**, and enter ```
emerald --replace
``` and then go to: **Main Menu > System > Preferences > Sessions > Options** tab, and click on **Remember Currently Running Applications**.

---

### Post by sdlynx on 2008-12-05
I have tried editing the settings under Appearance -> Visual Effects and it's already set to Extra.  "compizconfig-backend-gconf" is installed, and so is fusion-icon (and I have it set under sessions to start up).

I tried using sudo ccsm and I was able to correctly change the settings, so I checked the configuration file and it is read and write accessible by "Owner (me)".  so now I think it is a permissions problem but don't see how.

---

