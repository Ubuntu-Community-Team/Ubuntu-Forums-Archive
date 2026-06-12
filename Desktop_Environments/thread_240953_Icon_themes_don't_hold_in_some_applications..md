---
title: "Icon themes don't hold in some applications."
date: 2006-08-21
forum: Desktop Environments
---

### Post by Bastanteroma on 2006-08-21
Some programs (Synaptic, for example) seem to stick to the default Gnome icons, even for basic things like the close button, no matter which icon set I choose.  EDIT- I realized that I need to change the icon set used by programs running as root.  I'm trying now to figure out how.

EDIT Again- I tried running the gnome theme manager as root and changing the icon theme, but no luck.

Thanks
SOLVED

---

### Post by Noramskull on 2006-08-22
It's quite possible that the icon themes you have downloaded contains multiple icon sets which the gnome theme manager can't handle. 

Instead I would suggest that you unpack the icon themes manually into ~.icons or if you want to do it systemwide then /usr/share/icons

After that, select the theme in the theme manager as you would have done otherwise. I think that should take care of your problem.

---

### Post by mcduck on 2006-08-22
You are right about those apps running as root instead of yourself.

To make root apps use the same themes, icons & fonts that you are using, run these 3 commands in a terminal:
```

sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.fonts /root/.fonts
```
That makes links from your icons, themes and fonts directories to root's home. Now root has all the same themes you have, and automaticly uses the same themes you use :)

---

