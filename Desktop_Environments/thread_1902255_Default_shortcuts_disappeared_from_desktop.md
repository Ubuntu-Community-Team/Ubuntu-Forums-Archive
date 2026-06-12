---
title: "Default shortcuts disappeared from desktop"
date: 2011-12-30
forum: Desktop Environments
---

### Post by Bartender on 2011-12-30
Good morning!
I've been dinking around with CairoDock and Docky this morning.  Docky seemed good enough so I uninstalled Cairo.  At some point (not sure when exactly) the default Xubuntu shortcuts that should be visible on the upper left of the desktop left the building.  

If I go to Settings>Settings Manager>Desktop, then click on "Icons" tab, the Home, Filesystem, Trash, and Removable Devices icons are listed and checked.

I imagine new ones can be created if I can figure out how, but I'd rather find out why the icons that the system says are there are not.

---

### Post by Toz on 2011-12-30
In that same dialog box (Settings>Settings Manager>Desktop, then click on "Icons" tab), what do you have selected in the "Icon Type" drop-down? I believe it needs to be set to File/launcher icons. If it is, try setting to something else and back again.

Also, xfdesktop needs to be running for the icons to be displayed. From a terminal window:
```
ps -ef | grep xfdesktop | grep -v grep
```

---

### Post by Bartender on 2012-01-02
Hi, Toz -
Apparently what happened is I lost the icons when I asked Compiz to take over.  I went back to xfce (that's not exactly what it's called in the choices but you know what I mean).  I think I had to reboot?  Anyway, once I was using xfce to draw the desktop the three default icons came back.  But the text was huge!

I was able to fix that by going into xfce4-settings-editor and finding the part about icon text size.

---

