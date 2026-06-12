---
title: "Screen freezing!"
date: 2006-09-02
forum: Desktop Environments
---

### Post by epb on 2006-09-02
I've just installed the graphics driver for my Radeon 9700 card (by help from these forums) and afterwards i've encounted some problems: sometimes my screen freezes and the top panel on the desktop gets blurred, or the screen just goes black. For example when I press ctrl+alt+f1 and use the terminal and then switch back to the desktop... it freezes! Or when I log out to log-in as another user, the login screen never appears.. instead the screen just goes black!

Any help on this? Maybe the new driver causes the problem?

---

### Post by epb on 2006-09-03
I forgot to mention that the driver I was using is 'flgrx'. Now I've tried to use the "radeon" driver instead (I pasted it in the xorg.conf file where it previously said "flgrx") and it seems to work a bit better. But when I enter

```
glxinfo | grep direct
```

in the terminal it tells me that "direct rendering: no", so the driver is not working correctly, right? I've done some searching on the forums, but I can't seem to find a manual to turn on the direct rendering... Please help!

(Sorry, for being a little too fast on placing this thread in the Desktop Support forum instead of the Video & Sound forum! :oops: Anyway I can move it?)

---

