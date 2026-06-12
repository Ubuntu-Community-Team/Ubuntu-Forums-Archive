---
title: "ctrl-alt-f1"
date: 2007-10-18
forum: Desktop Environments
---

### Post by tienhn on 2007-10-18
I am on a T61p laptop with NVIDIA display.

CTRL-ALT-F1 to F6 does not switch to a console login any more. Anyone has the same problem?

Cheers,

---

### Post by rahimveron on 2007-10-22
Ya i have the same problem. It does not switch to command line console console. Still waiting for the solution here.

---

### Post by jespdj on 2007-10-22
Maybe those keys are now assigned to some other function? It could be assigned to one of the Compiz functions. Install the Compiz configuration settings manager:
```
sudo apt-get install compizconfig-settings-manager
```
You'll get a new menu item System / Preferences / Advanced Desktop Effects Settings, in which you can configure all the Compiz plug-ins. Especially look at the "Actions" settings of the plug-ins that are enabled; there, the keys assigned to the plug-in are listed. Maybe ctrl-alt-f1...f6 are connected to one or more plug-ins.

---

