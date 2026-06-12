---
title: "no gnome session file?"
date: 2011-08-30
forum: Desktop Environments
---

### Post by Doggerdoo on 2011-08-30
when i select gnome session from login screen, there is only the cursor and the desktop background. :mad:but when i select failsafe gnome it works! i've tried looking at home/.gnome/ for the session file but theres is none. :(

---

### Post by Doggerdoo on 2011-08-30
Please Help!

:frown:

---

### Post by Frogs Hair on 2011-08-30
When you log-in to the Gnome session try to open the terminal using  Alt +F2 . Enter ```
gnome-terminal
```If the terminal opens for you run the following ```
gnome-panel
```If that fails use the following to restart the panel , as strange is it may be the panel can be running without being visible .```
killall gnome-panel
```

---

### Post by Krytarik on 2011-08-30
This, for a start, but I suggest opening the Terminal straight away by pressing Ctrl+Alt+T, because the Alt+F2 dialog is a feature of Gnome Panel, thus unlikely to work if you can't even see them.

There are multiple reasons for the Gnome Panels not coming up at login. So, if the above method brings them up, you'll need to dig a bit deeper.

Greetings.

---

### Post by Doggerdoo on 2011-08-31
i ended up just re-installing ubuntu, and now it works!!

:P :P :P :P :P :P

---

