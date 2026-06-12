---
title: "New install, desktop doesn't work"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Massive Brain on 2006-01-29
New computer, new Ubuntu install. All packages are up to date.

The system locks up when starting Gnome. Brown screen with mouse cursor, everything except the cursor is dead. The only thing to do is to reset.

Instead I try to run openbox, it works but the system locks up when starting Firefox, all I see is an empty Firefox window, everything but the mouse cursor is dead.

Windows Server 2003 just works.


System:
A64 X2 3800+
Gigabyte GA-K8N-SLI (nForce4 SLI)
Geforce 6600LE

---

### Post by bonzodog on 2006-01-29
It sounds like an xorg problem. you will need to edit xorg.conf find out what driver it is implementing, but I would try shifting it from "nv" to "vesa". Also, install the nvidia-glx package, that might sort out the issues with the card. There are instructions on installing the nvidia 3D drivers on here somewhere.

---

### Post by Massive Brain on 2006-01-29
Thanks, that's what I think too. Will try.

---

### Post by Massive Brain on 2006-01-29
It's working quite nicely now, thanks.

---

