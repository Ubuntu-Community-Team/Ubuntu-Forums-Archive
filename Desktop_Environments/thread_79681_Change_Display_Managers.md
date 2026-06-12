---
title: "Change Display Managers?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by NMUrugbysteve on 2005-10-20
Is there any way to change from GDM to a lighter display manager, such as WDM? If not that, anyone want to tell me how to get rid of a display manager altogether so that i just type startx?

---

### Post by Ampersand on 2005-10-20
either open Synaptic and install wdm, or run:
```
sudo apt-get install wdm
```
and you'll be prompted to set a default display manager.

To change at a later date, run:
```
sudo dpkg-reconfigure wdm
```

---

