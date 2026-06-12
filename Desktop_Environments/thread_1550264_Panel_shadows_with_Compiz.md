---
title: "Panel shadows with Compiz"
date: 2010-08-10
forum: Desktop Environments
---

### Post by thaelim on 2010-08-10
Does anybody know where the option is that controls the gnome panel shadows? I have two PCs both running identical themes on Lucid. One has shadows on the panels, the other doesn't. I've tried reinstalling the theme and resetting all the Compiz settings to default using CCSM, but it didn't make any difference.

---

### Post by stinkeye on 2010-08-10
> **thaelim said:**
> Does anybody know where the option is that controls the gnome panel shadows? I have two PCs both running identical themes on Lucid. One has shadows on the panels, the other doesn't. I've tried reinstalling the theme and resetting all the Compiz settings to default using CCSM, but it didn't make any difference.

CCSM > effects > window decoration > shadow windows

To shadow all windows includung gnome-panel use
```
any
```



To shadow all except gnome-panel use
```
(any) & !(class=Gnome-panel)
```

---

### Post by thaelim on 2010-08-11
Yup that was the first place I looked, and those settings were already correct (those are the default values, and I did a full reset-to-defaults). However it seems the RGBA module I was using for GTK was the cause of the problem, disabled that and the shadow came back. Now just have to figure out why metacity is giving me transparency on one machine and not the other...

---

