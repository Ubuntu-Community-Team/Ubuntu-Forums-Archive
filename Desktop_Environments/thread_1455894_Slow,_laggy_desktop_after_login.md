---
title: "Slow, laggy desktop after login"
date: 2010-04-16
forum: Desktop Environments
---

### Post by kflorence on 2010-04-16
Hello all.  I'm running a Dell Optiplex 330 machine here at work with an NVIDIA Quadro NVS 285 with 2 screens (a BenQ and an Acer) connected with a DVI-D Y splitter cable.  I've been having this very strange problem when logging into GNOME on 9.10 (problem did not exist in 9.04) -- after the desktop loading screen, everything becomes very slow, laggy and unresponsive.  If I boot into GNOME failsafe, everything runs fine...

I've been getting around this problem by doing the following after the desktop is visible: switching to TTY-1 (ctrl+alt+1), then switching back to X (ctrl+alt+7), this fixes the lag and there are no further problems until the next bootup.

I have tried changing the NVIDIA drivers (currently using the recommended version 195 NVIDIA driver) and reconfiguring X config settings, which seemed to fix the problem, but on the next reboot it remained (even though the settings were still changed).

I attached my X conf and logs below, let me know if you need anything else that may help diagnose the problem.

---

### Post by kflorence on 2010-04-19
bump

---

### Post by itbcn8 on 2010-05-31
I'm having the same problem!
I log in, brand new install of Ubuntu 10.04 (through Wubi)...

And all of the sudden everything is slow and laggy.
My windows partition on this same computer runs great... so this is not a good sign for Ubuntu.

Anyway, I checked my memory and CPU usage. The RAM usage is normal and consistently underused (1.5Gb total), but my 2 CPU cores seem to alternate hitting 100% for a second (I guess enough to bottleneck everything and causing lag).

This is especially problematic because I can't stay in Ubuntu to troubleshoot (wayyyy to slow). So I don't know what you guys can do to help...

Please advise something...

---

