---
title: "SLED10 XGL/compiz in ubuntu"
date: 2006-07-19
forum: Desktop Environments
---

### Post by finalbeta on 2006-07-19
Currently I can't really run XGL due to the variaty of bugs (windows not drawing after comming from tray, openGL games not working, Java apps not drawinf, remote desktop to windows looking freaky) etc etc. Quinns packages have options, but are unstable, the vanilla ones are stable, but you can't even place a window on top.

Some of these issues have been fixed in SLED10, for example the Java one. Can the XGL / compiz from sled be ported to ubuntu, will packages come available, or how does this work?

---

### Post by gamma on 2006-07-19
If you can get a hold of the source code for SLED's XGL then you can compile it yourself and pray it works. As far as OpenGL games go, it's recommended that you play outside of XGL by typing DISPLAY=:93 gamenamehere for nvidia. More info at compiz.net if that doesn't work.

I'd keep trying quinn/vanilla packages and hope everything works. Get gset-compiz and see if removing any plugins fixes the java issue.

---

