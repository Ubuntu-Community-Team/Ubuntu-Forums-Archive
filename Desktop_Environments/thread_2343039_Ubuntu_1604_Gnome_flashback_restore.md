---
title: "Ubuntu 16:04 Gnome flashback restore"
date: 2016-11-12
forum: Desktop Environments
---

### Post by James Wilde on 2016-11-12
I'm running Ubuntu 16:04 and have installed Gnome flashback.  In the process of adding some regularly used icons to the panel, some of them appeared at the right hand end, including a duplicate of one at the left hand end.  I moved the ones I needed, and set out to delete the duplicate icon, but instead of just that icon, all the right hand end panel disappeared, the one with the power button, the sound and wifi icons, the clock and all the rest.

Is there some easy way to restore the default settings?  Alternatively is there any way to recreate that panel and put the icons on it?

1k thanks in advance.

---

### Post by CantankRus on 2016-11-13
This will reset gnome-panel.
```
dconf reset -f /org/gnome/gnome-panel/
```

When testing I had no **clock** or **user** applet to the top right so you may have to re-add.

****Edit**: What I found was I didn't have indicator-applet-complete installed.
This contains all the right hand menu items and after installation was available in the panel applets and
the command above reset the panel to default..... ie showing time, date etc to the right.

---

### Post by James Wilde on 2016-11-13
Great, CantankRus.  That did it for me.

Thanks!

---

