---
title: "Accidental Deletion of Top Panel"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Holy_Nexus on 2009-10-30
I accidentally deleted the top panel. I was able to put one back, I'm having trouble getting some of the applets back, particularly the NetworkManager Applet and the Power Manager.  I'm still very new to this. What do I do?

---

### Post by Earl_Maroon on 2009-10-30
alt+f2 to get the run dialogue and try ```
nm-applet
``` for Network Manager. Repeat with ```
gnome-power-manager
```.

---

### Post by Holy_Nexus on 2009-10-30
> **Earl_Maroon said:**
> alt+f2 to get the run dialogue and try ```
nm-applet
``` for Network Manager. Repeat with ```
gnome-power-manager
```.

It didn't do anything.

---

### Post by Holy_Nexus on 2009-10-30
Nevermind. I found it, myself. Under Add-Panel, they're grouped together under the Notification Area.  Funny, I've been looking for days and didn't figure to look there--  Thanks for the help, anyway.

---

### Post by keplerspeed on 2009-10-30
One way is to delete all the gnome config folders in your home directory, however, this will remove your saved wireless settings, wallpaper settings etc. For this BE CAREFULL:
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```
This will reset all gnome configuration back to the defaults.

Otherwise you can add new panel and manually add everything back onto it. It sounds like you have worked out how to do that!

---

### Post by blazemore on 2009-10-30
nm-applet isn't on the notification area; it's a separate application.

If you want to revert your panel settings to default, hit Ctrl + F2 and type
```
gksu debconf gnome-panel
```
Then hit enter

---

### Post by keplerspeed on 2009-10-30
Hmm cool thats a better way of doing it!

---

