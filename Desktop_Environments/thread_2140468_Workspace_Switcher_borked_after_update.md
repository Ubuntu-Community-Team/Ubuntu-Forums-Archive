---
title: "Workspace Switcher borked after update"
date: 2013-04-29
forum: Desktop Environments
---

### Post by feffer on 2013-04-29
Running Ubuntu 12.04 w/Unity -- pretty much standard; using the "wall" and no compiz mods. After the recent update, workspace swither acts weirdly. The 4 spaces show up as 2 x 2, but the outline selects the 2 uppers together, and the 2 lowers together. Also when dialogs open they often go to the 2nd upper space instead of #1 space where the app is open. It is impossible to work. I tried going to compiz and using the cube, but Workspace Switcher still shows space 1 & 2 clumped together and space 3 & 4 as well. I tried to fix it with gconfig-editor, but could not. Does gconfig-editor require a restart to do this? Is there a way to reconfigure the WS? I'm OK with command line. What to do?

---

### Post by Frogs Hair on 2013-04-29
I am in XFCE at the moment , but try CCSM > General >  General Options > Desktop Size.

---

### Post by feffer on 2013-04-29
Yah, I've tried that using both the Wall and 2 x 2, and the Cube with 4 x 1. No effect at all on the Workspace switcher. This was working fine for months, but after the update is borked. Can't find any setting to restore it.

In the past, dpkg-reconfigure has helped me, but I don't know if that fits here, and if it does what app to reconfigure.

---

### Post by Frogs Hair on 2013-04-29
You can view the update history in the software center and if you know what day the change occurred you could narrow what update/s it may have been.

Reset Compiz if needed: ```
dconf reset -f /org/compiz/ 
```

---

### Post by feffer on 2013-04-29
hmm, was that right? I don't think " /org/compiz" is a path...

---

### Post by feffer on 2013-04-29
We'll let me ask it this way, if I wanted to re-install the workspace switcher, what is that part of? What would I have to re-install?

---

### Post by Frogs Hair on 2013-04-29
I was thinking you were on 12.10 but after checking the reset command is the same for Compiz in 12.04. Unity reset is different though.

```
unity --reset
```

The switcher Is part of unity which is Compiz plug-in.

---

