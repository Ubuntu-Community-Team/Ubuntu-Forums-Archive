---
title: "Setting default/login resolution (10.04)"
date: 2011-06-14
forum: Desktop Environments
---

### Post by PenguinLust on 2011-06-14
When my system starts it has what I think is too high a resolution for my monitor (didn't think that was possible w/modern PnP!) How do I set it to the resolution I want for the login screen? All the advice I get sends me to /etc/X11/xorg.conf but there isn't one.
I'm running Ubuntu 10.04.

---

### Post by jony121 on 2011-06-14
You are letting software decide what's good for you.
sudo Xorg -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf

Find where is states the default resolution and change it to something you prefer. restart.

---

### Post by PenguinLust on 2011-06-14
When do I run
```
sudo Xorg -configure
```? It just gives
> Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


---

### Post by PenguinLust on 2011-06-15
Well, I guess I'll never know.

---

