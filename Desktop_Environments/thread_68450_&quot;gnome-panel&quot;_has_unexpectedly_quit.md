---
title: "&quot;gnome-panel&quot; has unexpectedly quit"
date: 2005-09-23
forum: Desktop Environments
---

### Post by @jens on 2005-09-23
Hello

after starting Gnome a window pops up with an error message:

The "Gnome-panel" has unexpectedly quit." On the botton panel the icons aren't clickable anymore and the upper panel is empty.  Clicking on "Restart application" or even X-restart don't help. Any ideas?

Thank's a lot

Jens

---

### Post by lisje on 2005-09-23
[QUOTE=@jens]Hello

after starting Gnome a window pops up with an error message:

The "Gnome-panel" has unexpectedly quit." On the botton panel the icons aren't clickable anymore and the upper panel is empty.  Clicking on "Restart application" or even X-restart don't help. Any ideas?

Thank's a lot

Jens[/QUOTE]
 have you tried reinstalling the gnome-panel?

---

### Post by fordfan753 on 2005-09-23
[QUOTE=@jens]Hello

after starting Gnome a window pops up with an error message:

The "Gnome-panel" has unexpectedly quit." On the botton panel the icons aren't clickable anymore and the upper panel is empty.  Clicking on "Restart application" or even X-restart don't help. Any ideas?

Thank's a lot

Jens[/QUOTE]

```
killall gnome-panel
``` 
for a quick fix, I'm not sure this would work permanently though. Try deleting everything off that panel, then restarting gnome, maybe something that's on the panel is causing it to die, some applet.

---

