---
title: "Screenshot of KDM sign&#8208;in screen"
date: 2008-04-21
forum: Desktop Environments
---

### Post by Aleksandersen on 2008-04-21
How&#8208;to capture a screenshot of the sign&#8208;in screen in KDM/KDE?

---

### Post by kellemes on 2008-04-21
Ctrl-Alt-F1 for other console and run..

```
xwd -display :0 -root | convert - png:kdmscreenshot.png
```

---

### Post by spupy on 2008-04-21
Or you can use [xnest]("http://en.wikipedia.org/wiki/Xnest").

---

### Post by Aleksandersen on 2008-04-21
Both commands returns that the display at :0 cannot be connected.

---

### Post by warp99 on 2008-04-21
Well you haven't logged into KDM yet so I assume that the owner is still root, therefore try to run a sudo in front of the commands.

---

### Post by Aleksandersen on 2008-04-21
I was running the commands as root. So it had nothing to do with permissions.

---

### Post by aysiu on 2008-04-21
Run Kubuntu through VirtualBox - that's another option.

---

