---
title: "Changing Properties On Application Launch Bar"
date: 2009-03-23
forum: General Help
---

### Post by crokett on 2009-03-23
Not sure what else to call it, in XP it would be the Start bar, but anyway, I was playing with the settings and made it small and autohide.  I can live with the small but don't like the autohide.  However, there is no room between icons on the bar to get preferences to change it back.  I looked in Preferences-Appearance, Compiz and Main Menu but don't see any settings there.  How can I change it back?

---

### Post by drs305 on 2009-03-23
Try running this:
```
gconftool-2 --set --type=bool  /apps/panel/toplevels/top_panel_screen0/auto_hide 'false'
```

If that is not the panel you want, open gconf-editor and go to /apps/panel/toplevels , find the correct panel and untick "autohide".
```

gconf-editor /apps/panel/toplevels

```

(See next paragraph before actually doing this). If this doesn't work for you, select one of the larger icons, such as the clock, and remove it to give you enough space to right click on an empty space on the panel. You can restore it after you make your panel changes.

Bonus tip: You can save the panel settings and restore them later.
Example to file ~/Desktop/panels:
```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
	
To restore saved panel settings and refresh the panel (example from file ~/Desktop/panels) :
```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

---

### Post by crokett on 2009-03-23
That fixed it.  Thanks

---

### Post by crokett on 2009-03-23
Ok the instructions sorta worked. I thought of removing icons on the  top panel before I posted the OT but all that did was shrink it further.  after trying the gconf-tool, it locked the laptop up so I had to reboot.  When I did, the panel was unhidden but the clock, notifcation tray, etc were all on the left.  I want them on the right. I tried messing with properties but could not get them moved. I ended up dumping the panel of my machine at work and loading it on this one, that worked.

---

### Post by drs305 on 2009-03-23
[QUOTE=crokett;6944035I thought of removing icons on the  top panel before I posted the OT but all that did was shrink it further.[/QUOTE]
Just for future reference: To prevent the panel from shrinking when an icon is removed you can make it span the entire width with:
```
gconftool-2 --type bool --set /apps/panel/toplevels/top_panel_screen0/expand 'true'
```

Normally you can position an icon where you want by right clicking on it, making sure "lock" is not ticked, and then moving it where you want, then "locking" it in position. You can't move it past another "locked" icon, which would have to be unlocked first.

---

