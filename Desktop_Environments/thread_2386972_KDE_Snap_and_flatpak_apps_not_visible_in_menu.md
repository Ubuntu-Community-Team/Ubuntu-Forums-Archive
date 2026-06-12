---
title: "KDE Snap and flatpak apps not visible in menu"
date: 2018-03-13
forum: Desktop Environments
---

### Post by luski on 2018-03-13
Hi,

when I install snap and flatpak apps, I can launch them only using terminal. But their desktop launchers are there in the /var/lib/flatpak/exports/share/applications and /var/lib/snapd/desktop/applications respectively. So when I'm moving these files to ~/.local/share/applications they are available in the KDE Menu, but I don't want to do it every time when I install anything from snap or flatpak. Do you guys have any idea how to solve this problem?

---

### Post by T.J. on 2018-03-13
I would not expect them to update the files used to generate KDE's menus as flatpaks are not part of the native package system.  Your best bet is to locate the install path and then add them yourself with KDE's menu editor.  

They will only be visible on your account but it will fix the problem.  As a programmer, I can tell you that neither Windows nor Linux guarantee that menus are updated unless the person who packaged the files takes the effort to do so.  Flatpaks compared to DEBs are relatively new, and I wouldn't expect everything to work out of the box just yet.

---

