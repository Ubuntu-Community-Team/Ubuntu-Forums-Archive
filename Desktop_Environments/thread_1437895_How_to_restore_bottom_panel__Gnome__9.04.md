---
title: "How to restore bottom panel / Gnome / 9.04"
date: 2010-03-24
forum: Desktop Environments
---

### Post by raymondh on 2010-03-24
I deleted the bottom panel when I switched to AWN.  

If I decide to.... how can I revert/restore to the default gnome desktop?  I can add a bottom panel but can't remember what applets go into it.

A friend wants to buy this laptop and may prefer the default, original gnome desktop.

Thanks in advance.

Raymond

---

### Post by onyxwolf on 2010-03-24
Can't think of a way to restore it, but the applets are (in order as was default) Show Desktop Button; Window List; Workspace Switcher; and Trash Applet, but isn't default kinda boring?

---

### Post by nitstorm on 2010-03-24
you can restore the default by right clicking the panel on the top and then click on New Panel :)

---

### Post by t.rei on 2010-03-24
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

this executed in terminal will reset all the panel attributes to 'ubuntu default' (they will be recreated when not found in config)

---

### Post by raymondh on 2010-03-24
Thanks all.

Though I am a AWN fan, buyer may choose/prefer the default desktop.

Thanks again.

Raymond

---

### Post by hyperzahranism on 2010-05-01
> **t.rei said:**
> ```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

this executed in terminal will reset all the panel attributes to 'ubuntu default' (they will be recreated when not found in config)

Thank you t.rei

you saved my life


> **raymondh said:**
> Thanks all.

Though I am a AWN fan, buyer may choose/prefer the default desktop.

Thanks again.

Raymond

I like docky most 60% of ubuntu users like it according to OMGubuntu

---

