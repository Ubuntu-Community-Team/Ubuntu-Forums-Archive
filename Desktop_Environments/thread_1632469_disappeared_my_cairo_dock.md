---
title: "disappeared my cairo dock"
date: 2010-11-28
forum: Desktop Environments
---

### Post by karrank% on 2010-11-28
While tweaking the settings on my cairo dock I seem to have made it disappear. Anyone know where to start looking to restore it? 

Thanks for looking.

Lucid 10.04.

---

### Post by tom4everitt on 2010-11-28
Try 

```

sudo apt-get purge cairo-dock
sudo apt-get install cairo-dock

```

Messed up settings are often solved by reinstallation :) There is probably some config file you can delete also, but I didn't have time to locate it.

---

### Post by karrank% on 2010-11-28
Thanks! Unfortunately the issue persists, I was originally trying to adjust the position, and I can see it flicker a bit off in the corner when I attempt to launch, but can't access it.

Forgot to mention I've been running full Compiz no problem, don't know if that's pertinent. 

Tried looking over at glx-cairo.org but don't know enough French for that to be helpful.

---

### Post by tom4everitt on 2010-11-28
Hmm, okay, well I see that cairo-dock is distributed across several packages; perhaps reinstalling them all will help? 

Search for cairo-dock gives: 

cairo-dock cairo-dock-core cairo-dock-data cairo-dock-dev cairo-dock-plug-ins cairo-dock-plug-ins-data  cairo-dock-plug-ins-integration 

I guess the setting could be in any of them. Just search for cairo-dock in Synaptic, remove them (fully), install them. There may also be a settings file in your home folder, which may be unaffected by reinstallation. To determine whether that is the case, create a new user and see if that user has the same problem. 

Because, it can hardly be anything other than a setting that is causing your problem. So resetting everything should work!

---

### Post by karrank% on 2010-11-28
create a new user and see if that user has the same problem.

Just what I was about to do. 

Thanks for the help.

---

### Post by karrank% on 2010-11-29
Ok, added a new user which exhibits no probs w/ Cairo dock....but ....

I think I caused this problem by mistakenly adjusting the "distance to screen edge" to negative 200 or so pixels. Is there is some way of correcting this via CLI or terminal?

('Cos I've screwed up the GUI  enough to lose that capacity.)

Would be more educational than just whipping out a new user.

-Anyway, thanks for helping.

---

### Post by karrank% on 2010-11-29
solved! lateral offset reset to -1 (instead of -1000 !!) in config file inside of CURRENT THEME

Relief--don't feel like such a moron now.

---

