---
title: "Cinnamon - unable to change window theme"
date: 2012-07-15
forum: Desktop Environments
---

### Post by Shadius on 2012-07-15
Hey everybody! :) 

Basically, the Window theme in Cinnamon Settings is not changing to any other theme other than Adwaita. Any solution to this? I've included a screenshot of my Cinnamon Settings.

---

### Post by lolpenguin on 2012-07-15
It is on Adwaita in the screenshot, so it will show as Adwaita.
If you change the window theme, Cinnamon needs you to restart the shell, since that bug was not fixed in Cinnamon but was in GNOME.
Alt + F2, type r, then enter/return.
If that doesn't work, then open a terminal.
```
gsettings set org.cinnamon development-tools true
```
Then try again.

(made a mistake, the gsettings schema should be org.cinnamon not org.gnome.cinnamon. for future uses anyway)

---

### Post by Shadius on 2012-07-15
> **lolpenguin said:**
> It is on Adwaita in the screenshot, so it will show as Adwaita.
If you change the window theme, Cinnamon needs you to restart the shell, since that bug was not fixed in Cinnamon but was in GNOME.
Alt + F2, type r, then enter/return.
If that doesn't work, then open a terminal.
```
gsettings set org.gnome.cinnamon development-tools true
```
Then try again.

Ah, thanks! The problem was that I didn't restart Cinnamon after selecting my desired window theme. It didn't occur to me to restart Cinnamon since I could change the GTK+ theme and have it applied upon selection without restarting Cinnamon. Thanks again.

---

