---
title: "Visual Effects Problem"
date: 2009-09-16
forum: Desktop Environments
---

### Post by nezurian on 2009-09-16
Hello.

I am using Nvidia GeForce MX 440 graphics card. I installed it's driver to make visual effects working. But When I improve the effects, the bar that has the title of the program we use ( I don't know it's name sorry ) (you know, like the upper bar of the application window) disappears. 

Any suggestions ?

---

### Post by drs305 on 2009-09-16
Assuming you are using Compiz, install the CompizConfiguration Settings Manager via Synaptic or command line:
```

sudo apt-get install compizconfig-settings-manager

```

To open from the menus, System, Preferences, CompizConfig Settings Manager.

If the titlebars are missing from all apps, try going to Windows Management, Place Windows, make sure it is ticked (enabled) and select the Smart option. If that doesn't solve the issue, try some of the other available options.

If you have no borders, make sure Effects, "Windows Decorations" is enabled.

---

