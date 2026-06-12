---
title: "nautilus view changed"
date: 2011-10-08
forum: Desktop Environments
---

### Post by malakar.subhendu on 2011-10-08
I have accidently removed all the toolbars from nautilus and now cannot work properly. Can anybody help me to restore those toolbars.

---

### Post by Copper Bezel on 2011-10-08
Are you saying that you don't have a menu bar at all, either? There's no option I know of to remove the menu bar itself, and the visibility of all of the other UI elements is controlled from the View menu.

---

### Post by WasMeHere on 2011-10-08
> **Copper Bezel said:**
> Are you saying that you don't have a menu bar at all, either? There's no option I know of to remove the menu bar itself, and the visibility of all of the other UI elements is controlled from the View menu.
Do you use 'vanilla' Ubuntu 11.04 or 11.10 with the Unity desktop? Then the top pulldown meny of the active window is on the panel at the top of the screen.

Can you press 'View' and get a pull down menu? In that case select various features until you get what you want. Otherwise something is wrong, and you can try to restore Nautilus to the default settings by removing and restoring the package.

---

### Post by Copper Bezel on 2011-10-08
Reinstalling the package will fix it if the package itself is broken. However, to reset your config, run ths:

```
gconftool-2 --recursive-unset /apps/nautilus
```

---

### Post by malakar.subhendu on 2011-10-08
> **Copper Bezel said:**
> Reinstalling the package will fix it if the package itself is broken. However, to reset your config, run ths:

```
gconftool-2 --recursive-unset /apps/nautilus
```
thanks for the help.
Resetting the configuration helped me.

---

### Post by malakar.subhendu on 2011-10-08
> **Copper Bezel said:**
> Are you saying that you don't have a menu bar at all, either? There's no option I know of to remove the menu bar itself, and the visibility of all of the other UI elements is controlled from the View menu.
I had removed the menubar and main toolbar view from the view menu itself.
So there was no main and menu toolbar at all.

---

### Post by Copper Bezel on 2011-10-08
Oh, wow, I've never seen that. Well, I'm glad the reset worked. = )

---

