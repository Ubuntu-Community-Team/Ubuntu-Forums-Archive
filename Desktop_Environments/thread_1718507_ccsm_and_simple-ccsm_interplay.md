---
title: "ccsm and simple-ccsm interplay"
date: 2011-03-31
forum: Desktop Environments
---

### Post by erikdstock on 2011-03-31
Hi- the subject pretty much says it. Well, first:

a) what does the green check mark do in simple-ccsm? It seems to undo all the settings changes I have made. And what is the "Advanced" Profile?

b) say i want to tweak something that simple-ccsm can't do. Slow down the animations so I can actually see them, enable or change edge snapping , et cetera. Does changing settings in this one disable my profile in simple? I seem to wreck everything whenever i try to work with ccsm but simple is just too simple--I'm not even looking for eye candy so much as functionality.
         b.0.1: can i do half screen snapping on the side like vista does?

thank you.

---

### Post by Copper Bezel on 2011-03-31
See [here]("http://ubuntuforums.org/showthread.php?t=1304261&highlight=aero+snap") for Snap. It involves installing something called wmctrl that will allow you to send commands to windows and setting Compiz edge bindings to those commands via CCSM. I recommend one change - don't use edge bindings, but button bindings instead, so that clicking an edge snaps the window; otherwise, it's easy to accidentally activate it by just brushing a screen edge. I also use the command 

```
wmctrl -r :ACTIVE: -b toggle,maximized_vert && wmctrl -r :ACTIVE: -b remove,maximized_horz
```

bound to an upper-edge click, which is almost as nice as the Maximize Vertically feature in Aero (which is itself a vast improvement on the same feature in Compiz.)

These are still not as nice as Aero's snap, because they depend on the cursor's position, not the window's.

Simple-ccsm will get you the basic settings, but it'll override your fine-tuning in Compiz. Once you have the basic settings you want, stop using simple-ccsm. You can save profiles from the real ccsm, too.

---

