---
title: "Remove GNOME Panel Border?"
date: 2009-07-15
forum: Desktop Environments
---

### Post by matthew.ball on 2009-07-15
Hi,

I was just wondering if it's possible to remove the border on a GNOME panel.

I have found I can make the top panel transparent, which blends in really nice with my desktop background, except, there's the panel border still visible..

I checked around gconf in apps/panel/ but I couldn't find anything.

Is it even possible?

Cheers

---

### Post by VCoolio on 2009-07-16
I think you mean the dropshadow. You can disable this in compiz if you're using that for individual apps. In system > preferences > compiz config settingsmanager (if you don't have it, install ccsm) go to window decorations plugin and in entry at bottom for shadow windows add exactly
```
!(class=Gnome-panel)
```

---

### Post by matthew.ball on 2009-07-16
Hah, that's perfect.

Thanks very much.

---

