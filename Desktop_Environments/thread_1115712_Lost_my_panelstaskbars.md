---
title: "Lost my panels/taskbars"
date: 2009-04-04
forum: Desktop Environments
---

### Post by kjl291 on 2009-04-04
Help! Through relentless screwing around I have managed to banish all taskbars/panels, and this ultimately happened to me both in Xubuntu as well as Ubuntu (and I don't really care for Kubuntu). I can open the file manager from the desktop and launch some apps that way, but other than that I am dead in the water. I have tried, for example, uninstalling and reinstalling Xubuntu (before I lost my panels in Ubuntu) with no luck. I cannot add/remove apps or do much of anything adminstrative or settings-wise. Any ideas? Thanks!

---

### Post by _Purple_ on 2009-04-04
For Ubuntu, type the following command in the terminal:
```
killall gnome-panel
```

---

### Post by soomro on 2009-04-04
this happend to me too when i customized a lot of compiz so i uninstalled restarted and installed again now they are fine.

P.S the windows went black not vanished at all. thanks

---

### Post by kjl291 on 2009-04-04
> **_Purple_ said:**
> For Ubuntu, type the following command in the terminal:
```
killall gnome-panel
```

did it, but it says ```
gnome-panel: no process killed
```

---

### Post by _Purple_ on 2009-04-04
You can check this [link](http://ubuntuforums.org/showthread.php?t=1115116).

---

### Post by UbuntuNerd on 2009-04-04
run this command it should restore both of your panels:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by yildiz.a on 2009-04-14
Thanks for advice, it worked!

---

### Post by Sargonos on 2009-04-21
hey, im new to linmux, and i experimented around with ubuntu before switching to xubuntu.

i like xubuntu better except for the "startbar"  :(  (sorry for the windows term)

any way what i would like is to get the ubuntu bar in xubuntu and get rid of my current one... is this doable??

or is this the difference between gnome and xubuntu's desktop???

if this makes no sense at all im sorry :(

zac

---

### Post by Sargonos on 2009-05-01
bumb help please???

---

### Post by PacSci on 2009-05-01
You might want to start a new thread for this...and spell "bump" right. I've got my Panel set up in an XP-like config right now, too. I'm assuming you're still using the two-panel system (one on top and one on bottom).

Delete the top panel, then remove everything from the bottom panel (don't delete it!). Right click on it, and select "Add New Items". To add an item, double-click it, From left to right, add an Xfce Menu, any Launchers for applications you want, a Task List, a Mixer if it's available, a Notification Area, and any of the Clocks ("Orage Clock" and "Clock" work well).

---

