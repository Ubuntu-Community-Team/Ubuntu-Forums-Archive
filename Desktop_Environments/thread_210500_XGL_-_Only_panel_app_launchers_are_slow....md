---
title: "XGL - Only panel app launchers are slow..."
date: 2006-07-07
forum: Desktop Environments
---

### Post by JedTheHead on 2006-07-07
XGL / ATI:

All is well and fast in Xgl / Compiz - except opening apps from the panel.  Anything started from the panel results in a slow box / outline opening and then the app opens.  This process is really slow and seems to be the only real slow-down.  Any ideas?

Thanks!

---

### Post by mcduck on 2006-07-07
> **JedTheHead said:**
> XGL / ATI:

All is well and fast in Xgl / Compiz - except opening apps from the panel.  Anything started from the panel results in a slow box / outline opening and then the app opens.  This process is really slow and seems to be the only real slow-down.  Any ideas?

Thanks!

open Configuration Editor (in applications/accessories, or run 'gconf-editor' in terminal), browse to apps/panel/global (if I remember right) and unmark the 'enable_animations'-key. That should disable those ugly wireframe animations for all panel launchers except the trash can (I have no idea how to disable that one).

---

### Post by JedTheHead on 2006-07-07
You rock.  Worked like a charm, now my ATI Xgl is smooth like butter.

Sorry for the double post, got a little anxious ;)

---

