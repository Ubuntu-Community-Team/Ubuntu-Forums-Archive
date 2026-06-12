---
title: "COMPIZ Keep KDE Plasma panel below windows"
date: 2022-01-09
forum: Desktop Environments
---

### Post by zemerdon2 on 2022-01-09
found this little beauty of a script which keeps the kde plasma panel below everything.

-----------------------------------------------------------------------------------------------------------------------------
#!/bin/bash
sleep 5
wmctrl -l | grep Plasma | awk '{print "wmctrl -v -i -r " $1 " -b remove,above"}' | bash
wmctrl -l | grep Plasma | awk '{print "wmctrl -v -i -r " $1 " -b add,below"}' | bash
-----------------------------------------------------------------------------------------------------------------------------

Im using Kubuntu 20.04, KDE Plasma v5.18.5, Kernel 5.11.0-44-generic, Compiz v0.9.14.1, Emerald v0.8.16, Nvidia drivers v495.46.

Everything working perfectly.

---

### Post by mIk3_08 on 2022-01-09
> **zemerdon2 said:**
> found this little beauty of a script which keeps the kde plasma panel below everything.

-----------------------------------------------------------------------------------------------------------------------------
#!/bin/bash
sleep 5
wmctrl -l | grep Plasma | awk '{print "wmctrl -v -i -r " $1 " -b remove,above"}' | bash
wmctrl -l | grep Plasma | awk '{print "wmctrl -v -i -r " $1 " -b add,below"}' | bash
-----------------------------------------------------------------------------------------------------------------------------

Im using Kubuntu 20.04, KDE Plasma v5.18.5, Kernel 5.11.0-44-generic, Compiz v0.9.14.1, Emerald v0.8.16, Nvidia drivers v495.46.

Everything working perfectly.

Wow! cool stuff. Thanks for sharing. This may help to everyone who will use same combination of environment as you do. Good Luck and Cheers.

---

