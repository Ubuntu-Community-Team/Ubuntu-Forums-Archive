---
title: "XFCE problem"
date: 2005-04-22
forum: Desktop Environments
---

### Post by Nob on 2005-04-22
i installed XFCE as my default session...
but there is problem, in xfce, xmms isnt working, it cant play songs [in gnome everything is fine]...

anyone know whats the problem?

output driver is set correctly [same as gnome]... 
and yes, i checked "Load GNOME blabla on XFCE startup" rebooted few times, still music isnt working...

---

### Post by soce_32 on 2005-04-23
You probably have esd running under gnome, but not under xfce.  xmms is probably set for esd output.  Try running esd under xfce and see if you get sound.

---

