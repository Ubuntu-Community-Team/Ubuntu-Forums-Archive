---
title: "kdm crashes graphics"
date: 2012-04-07
forum: Desktop Environments
---

### Post by ChopstickNINJ4 on 2012-04-07
Hi all,

Not sure how to fix this, but pretty sure it's a bug.  I install Kubuntu with wubi and on initial boot gets to the dots part of loading Kubuntu, but as soon as KDM kicks in the entire screen flashes to a static/grid garbage pattern.  I can move my mouse and the mouse cursor renders properly on top of KDM which is weird, but everything else is borked.

Running an HD 5850 for graphics.

Thanks!

---

### Post by Zorael on 2012-04-08
Is kdm properly installed? (**sudo apt-get install --reinstall kdm**)

Is anything of interest output to **/var/log/kdm.log** and/or **/var/log/Xorg.0.log**?

What are the contents of **/etc/X11/default-display-manager**?

What does the **/etc/alternatives/x-session-manager** symlink point towards?

---

### Post by ChopstickNINJ4 on 2012-04-10
Ah... I already switched away from Wubi and had no issues with an install using a partition.  Thanks though!

---

