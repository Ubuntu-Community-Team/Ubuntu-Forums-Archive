---
title: "Restarting GDM (log out/log on) leaves duplicate processes running"
date: 2009-11-05
forum: Desktop Environments
---

### Post by yurx cherio on 2009-11-05
I am running Karmic 64AMD.

Whenever I choose "Log Out" to restart GDM when I log back in I can see that all processes started by the previous GDM session are still there alone with the new ones spawned when I log in. Next thing I do I log back out and in again. Now I have triplets.

Can it be explained in a rational way? I think it is a bug. Why do I need processes like evolution-data-server, gnome-pty-server, etc running in multilpe instances? Although most of processes launched by GDM are probably checking if another process instance is already running some of them are still re-launching duplicate copies.

Has anyone else noticed this?

---

### Post by CJN on 2010-01-29
I also get this behavior, though I just kill the duplicate processes (so far without consequence).

---

