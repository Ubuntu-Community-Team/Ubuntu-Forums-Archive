---
title: "conky alignment problem under compiz"
date: 2009-11-20
forum: Desktop Environments
---

### Post by rudeboyskunk on 2009-11-20
I've searched everywhere and can't find anybody else with this problem.  With compiz running, my conky falls underneath the gnome-panel.  I've got a screenshot attached.

---

### Post by VCoolio on 2009-11-21
Put "gap_y 30" in your config file to move it 30 pixels down.
You may also wish to add !(class=Conky) to the shadow windows entry in the window decoration plugin for compiz to prevent the dropshadows around conky.

---

