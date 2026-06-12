---
title: "wmctrl oddity on dual monitors"
date: 2011-05-19
forum: Desktop Environments
---

### Post by DavidBiesack on 2011-05-19
I have dual monitors (both 1600x1200) and X is set to span them. I prefer to set my Eclipse window to 3200x1100. However, when I use VNC to connect to my desktop, I'd have to pan around a lot, so I use wmctrl via a script to resize Eclipse (and Chrome, etc.) to better fit my smaller VNC viewport.

When I return to my dual-monitor desktop, I want to resize/move my windows again. But wmctrl does not work correctly. If I do

```
wmctrl -r 'Eclipse' -e 0,0,0,3200,1100
```

(from a script), then instead of putting the window at 0,0 and width 3200, the window appears on the second monitor (i.e. at 1600,0) with width 1600. So I must manually resize it which is more difficult.

Am I using wmctrl correctly? Is it not wmctrl's problem but my window manager? I'm using compiz in Ubuntu 10.10.

---

### Post by DavidBiesack on 2011-05-20
[https://bugs.launchpad.net/ubuntu/+source/wmctrl/+bug/454215](https://bugs.launchpad.net/ubuntu/+source/wmctrl/+bug/454215) may be related.

---

