---
title: "gnome panel HELP!!!"
date: 2008-11-11
forum: Desktop Environments
---

### Post by Awesomeness on 2008-11-11
i was installing some themes then the my computer got slow so restarted it when it started gnome there was nothing on the panels and i couldn't start any programs so i restarted my computer then changed it to xfce could any tale my how to get the panel working.
p.s alt+F2 doesn't work ether:confused::(:mad:

---

### Post by Coreigh on 2008-11-11
Did you interrupt the update when you rebooted? You may need to repair the package gnome-panel. In a terminal```
sudo dpkg --configure -a
```will fix incomplete updates. 

If the problem is specifically with gnome-panel```
sudo dpkg -i --reconfigure gnome-panel
```

---

### Post by acegik on 2008-11-11
try this it might help

gconftool --recursive-unset /apps/panel && killall gnome-panel


to refresh gnome panels

---

### Post by Awesomeness on 2008-11-11
> **Coreigh said:**
> Did you interrupt the update when you rebooted? You may need to repair the package gnome-panel. In a terminal```
sudo dpkg --configure -a
```will fix incomplete updates. 

If the problem is specifically with gnome-panel```
sudo dpkg -i --reconfigure gnome-panel
```

i doesn't work
it says (dpkg: unknown option --reconfigure)

---

### Post by Awesomeness on 2008-11-11
> **acegik said:**
> try this it might help

gconftool --recursive-unset /apps/panel && killall gnome-panel


to refresh gnome panels

it also doesn't work and it says (no process killed)

---

