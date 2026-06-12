---
title: "Enable mouse in terminal"
date: 2008-12-05
forum: General Help
---

### Post by ThaddeusW on 2008-12-05
Hello everyone, 

I want to enable the mouse in the system terminal on my Ubuntu server. I don't have X installed and want to use it in The Midnight Commander.

---

### Post by grim4593 on 2008-12-05
> General Purpose Mouse interface
This package provides a daemon that captures mouse events when the system
console is active, and delivers events to applications through a library.

By default, the daemon provides a 'selection' mode, so that
cut-and-paste with the mouse works on the console just as it does
under X.
```
sudo apt-get install gpm
```

Hope that helps.

---

