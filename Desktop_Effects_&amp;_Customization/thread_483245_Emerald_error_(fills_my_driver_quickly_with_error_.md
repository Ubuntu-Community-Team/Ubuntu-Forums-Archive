---
title: "Emerald error (fills my driver quickly with error logs)"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by nonameguy on 2007-06-24
(emerald:18768): Wnck-WARNING **: Unhandled action type (nil)


That is the error message I'm getting.  It happens quite often and all gets logged to .xsession-errors.  This happened last time I installed beryl, and again recentlly when I installed compiz fusion (and emerald again)

Please help, without emerald I get no window decoration.  With it, I get a HD full of error logs!

> 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


---

### Post by Happy_Man on 2007-06-24
So far as I can tell, the wnck-warning is normal, disregard it. 

The other error is in KDE, related to the fact that you don't have a Wacom tablet. Also harmless, disregard it.

---

