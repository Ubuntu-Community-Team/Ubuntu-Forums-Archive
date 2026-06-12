---
title: "CompizConfig SettingsManager Strange problem karmic 9.10"
date: 2009-11-08
forum: Desktop Environments
---

### Post by firedrake on 2009-11-08
Hello to everyone..  I have this VERY irritating behaviour..Compiz does not save settings between sessions..( I know there are other threads about this, please keep reading..)  1. All settings in CCSM remain the same between sessions..(nothing gets unchecked..) 2. Compiz Fusion Icon is set to auto start (and it does..) 3. window manager is compiz and window decorator gtk+  When I log out or restart none of the compiz settings work, but if I "Reload Window Manager" from the fusion icon drop down menu, everything works great..( up to next logoff or restart..)  Any help will be greatly appreciated, since it's been driving me crazy for days !!!

---

### Post by stinkeye on 2009-11-08
> **firedrake said:**
> Hello to everyone..  I have this VERY irritating behaviour..Compiz does not save settings between sessions..( I know there are other threads about this, please keep reading..)  1. All settings in CCSM remain the same between sessions..(nothing gets unchecked..) 2. Compiz Fusion Icon is set to auto start (and it does..) 3. window manager is compiz and window decorator gtk+  When I log out or restart none of the compiz settings work, but if I "Reload Window Manager" from the fusion icon drop down menu, everything works great..( up to next logoff or restart..)  Any help will be greatly appreciated, since it's been driving me crazy for days !!!
Try to load fusion-icon with the -n option in startup applications
This will make it start but not load a window manager.
Compiz should load anyway.
eg in the command box```
fusion-icon -n
```

---

### Post by firedrake on 2009-11-08
> **stinkeye said:**
> Try to load fusion-icon with the -n option in startup applications
This will make it start but not load a window manager.
Compiz should load anyway.
eg in the command box```
fusion-icon -n
```

Thanks..Same thing was happening before I even installed the icon, which I installed to load compiz on startup to save settings..:p  

Will try it when I get home and let you know...


EDIT :  It worked !! Thank you very much!  +1...

---

