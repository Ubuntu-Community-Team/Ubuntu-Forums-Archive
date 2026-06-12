---
title: "Compiz-Fusion + Nvidia Twinview = HUGE MAXIMIZATION"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by Metheos on 2007-07-30
Metacity seems to understand that my twinview setup is two monitors, and it will arrange windows and maximize them appropriately. Compiz-Fusion, however, throwns windows all over the place and Maximizes them across BOTH monitors... wtf?
Ubuntu 7.04 / Compiz-Fusion via Trevino repository
GeForce 7800 GS w/ TwinView enabled

---

### Post by Metheos on 2007-07-31
Found it, have to check the "Detect Outputs" box in the general settings.

---

### Post by KyleBrandt on 2008-02-25
I had to do the opposite:

Installed compizconfig-settings-manager

Then in System: Preferences: Advanced Desktop Effect Settings: General Settings: Display Settings Tab I UNchecked detect settings

I then added two entries under Outputs on the same tab:

1280x1024+0+0
1280x1024+1280+0

Hope this helps.

---

