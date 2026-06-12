---
title: "bukowski 0.9 theme....need help plz"
date: 2008-12-11
forum: General Help
---

### Post by ultratek on 2008-12-11
i am new as of today to linux and cmds....
i want to installl the bukowski theme which ends in .emerald and not .tar.gz

how do i do this?

---

### Post by blazemore on 2008-12-11
Well.
Emerald draws window borders, and requires compiz to run.
Firstly, ensure you have the right hardware drivers:
```
System -> Administration -> Hardware drivers
```

Reboot, and enable compiz: Right-click on the desktop, choose Change Background, go to the Visual Effects tab, and click Normal or the last one.

Should be using Compiz now, rather than Metacity.
Open a terminal and do:
```
sudo apt-get install emerald fusion-icon -y
```
Now go to System -> Preferences -> Sessions, and add a new startup entry:
```
Name: Fusion Icon
command: fusion-icon
comment: Load Compiz

```
Okay now hit alt+F2, and type fusion-icon and hit enter, to load a new icon in your notification area.
Right click the new icon, and choose Select Window Manager -> Emerald (or similar, it might call it compiz)

Your window borders will be ugly, but that's why you got the theme!

Now hit alt+F2 again and run emerald-theme-manager
Click Import, and browse to your theme
Select the theme in the emerald theme manager, and it should apply itsself to all windows.

Unfortunately, there's no centralised theme manager yet, although I did submit an idea to brainstorm somewhere...

---

