---
title: "stuck mouse (vmware on edgy)"
date: 2006-10-27
forum: Desktop Environments
---

### Post by dawm on 2006-10-27
just got vmware working so i can use XP from within edgy. i also installed vmware tools on the XP install, but randomly (it will happen but the timing is different each time) the mouse gets stuck and is unusable both in X and in  the vmware enviroment. and when i ctrl-alt-backspace to restart x the whole system hangs and i have to manually reboot the system via the power button.. anyone got any ideas? this only started to happen after i installed vmware tools on XP.

---

### Post by threespacemen on 2006-11-01
Dawm, are you running xscreensaver? I've found that occasionally (yet to determine the exact set of circumstances) if vmware has focus and vmware tools has captured the mouse (ie, it's become a windows pointer rather than your normal x pointer), when xscreensaver kicks in it has the tendency to magic away your pointer. 

Killing xscreensaver usually manages to kill the entire x session, however I've found that almost all of the time shifting focus away from vmware using the keyboard, then waiting for xscreensaver to kick in again usually returns the pointer.

Hope that helps...

---

