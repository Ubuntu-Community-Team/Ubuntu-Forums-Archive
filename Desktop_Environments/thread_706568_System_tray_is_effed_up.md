---
title: "System tray is effed up"
date: 2008-02-24
forum: Desktop Environments
---

### Post by y0umebednow on 2008-02-24
using ubuntu 7.10 

ok so the top panel with "Applications" "places" "System" is kinda screwed up.
on the right of the tray, it shows the network icon, my name, deskbar, volume control, and the date and time, and also the Quit.. icon which lets u logoff restart and such.

the problem with all those things on the right is that, i cannot click them, meaning its just an image that when i click, nothing happens. it lets me drag the whole panel if i hold and drag. but thats about it. when i try adding stuff to it, it just goes behind those useless icons which looks messed up.

can anyone help me resolve this issue please
thank you

---

### Post by Sam Lars on 2008-02-24
Try
```
killall gnome-panel
```
This will restart the panel.  If that doesn't fix it, would a screenshot help, or is it just that they won't respond to clicks?

---

