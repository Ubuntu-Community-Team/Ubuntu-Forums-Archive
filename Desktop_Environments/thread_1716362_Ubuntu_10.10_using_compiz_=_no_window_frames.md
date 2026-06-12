---
title: "Ubuntu 10.10 using compiz = no window frames"
date: 2011-03-28
forum: Desktop Environments
---

### Post by etopsirhc on 2011-03-28
ok i have compiz fusion set up for multiple desktop backgrounds , as well as a few other settings , but even after making sure that the window frame thing is enabled , it still doesn't show up . i t has been working up until just this morning. idk if an update happened or not but i know i didn't install anything new ( not including updates if it did )


**idk what happened , but i just restarted my computer and some how it all cleared up , @_@ **

---

### Post by 3Miro on 2011-03-28
The window frames are not done by compiz, but by a separate program. By default, the program is:
```
gtk-window-decorator
```
many people the shinier (and more resource consuming) emerald. If you suddenly lose the decorations, this means that the decoration component crashed. If this happens again, you don't have to restart your computer, you can simply hit Alt+F2 and type:
```
gtk-window-decorator --replace
```
depending on why one you are using
```
emerald --replace
```

```
compiz --replace
```
should also work as it will restart all components.

You can also install fusion-icon that will let you change window managers and decoration managers (if you want to use multiple ones).

Logout-login should also work (in place of a full reboot).

---

### Post by SS10house on 2011-03-28
If you do have the compiz icon

right-click and "Reload Window Manager"

this seemed to fix it for me

---

