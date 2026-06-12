---
title: "Accidentally removed autostart xfwm4 and xfce4-panel"
date: 2012-05-19
forum: Desktop Environments
---

### Post by acidrop on 2012-05-19
Hello

I have XUbuntu 12.04 and accidentally selected to not autostart
xfwm4 and xfce4-panel.So now the session loads but not the panels
so I cannot do anything even not alt+f2.

Tried removing ~/.cache and ~/.config to restore settings but that did not helped.

Where can add autostart entries for xfwm4 and xfce4-panel via console?

thank you

---

### Post by acidrop on 2012-05-19
ok  I found a solution by adding the following on 

/usr/share/xsessions/xubuntu-desktop:

Exec=xfwm4
Exec=xfce4-panel

---

