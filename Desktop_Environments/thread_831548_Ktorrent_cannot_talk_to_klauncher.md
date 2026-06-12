---
title: "Ktorrent cannot talk to klauncher"
date: 2008-06-16
forum: Desktop Environments
---

### Post by BetterSense on 2008-06-16
When I start my system up, sometimes I get this error message, and the ktorrent icon doesn't dock itself in the notification area properly, it occupies its own mini window on my desktop and I can't drag it up there or get rid of it. I don't run kubuntu but I run Ubuntu and have installed kubuntu-desktop.

---

### Post by p_quarles on 2008-06-17
Run the command below and restart ktorrent. This has solved the same issue for me many times. 
```
killall dcopserver
```

---

