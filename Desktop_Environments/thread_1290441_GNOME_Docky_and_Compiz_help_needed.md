---
title: "GNOME Docky and Compiz help needed"
date: 2009-10-13
forum: Desktop Environments
---

### Post by ScottNN on 2009-10-13
Hi,

I have some how managed to maximize the icons on my gnome docky bar.  I opened up the compiz bar and managed to hit a combination of mouse clicks that maximized the icons on the bar.  

Does any one have any ideas how to resolve this issue?  I think Compiz may be have done something...  I have tried removing and re-installing gnome do..

Thanks for your help.

Scott

---

### Post by stinkeye on 2009-10-14
> **ScottNN said:**
> Hi,

I have some how managed to maximize the icons on my gnome docky bar.  I opened up the compiz bar and managed to hit a combination of mouse clicks that maximized the icons on the bar.  

Does any one have any ideas how to resolve this issue?  I think Compiz may be have done something...  I have tried removing and re-installing gnome do..

Thanks for your help.

Scott
Can you not change the icon size buy right clicking on the gnome-do icon in the dock preferences > appearance.

---

### Post by ScottNN on 2009-10-14
Hi,  I don't have any option to change the icon size in the preferances -> appearance menu.   Random mouse clicking is dangerous!!!!!

---

### Post by stinkeye on 2009-10-15
> **ScottNN said:**
> Hi,  I don't have any option to change the icon size in the preferances -> appearance menu.   Random mouse clicking is dangerous!!!!!
Try changing the icon size in configuration editor
in terminal```
gconf-editor
```
then goto /apps/gnome-do/preferences/Docky/Utilities/DockPreferences
and change the icon size.
You will have to restart gnome-do.

---

### Post by ScottNN on 2009-10-15
Thank you!!! That worked!!!  Brilliant!!

---

