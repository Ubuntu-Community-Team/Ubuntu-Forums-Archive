---
title: "Lock Desktop Command in Gnome"
date: 2007-04-25
forum: Desktop Environments
---

### Post by n8wood on 2007-04-25
Can someone tell me what the command is to lock the desktop in gnome? My keyboard shortcut (Ctrl+Alt+L) isn't working so I want to create a custom one.

---

### Post by jordanmthomas on 2007-04-25
If you're using xscreensaver:
```
xscreensaver-command -lock
```

If you're using gnome-screensaver
```
gnome-screensaver-command --lock
```

---

