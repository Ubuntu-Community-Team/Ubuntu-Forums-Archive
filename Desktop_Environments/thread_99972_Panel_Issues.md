---
title: "Panel Issues"
date: 2005-12-06
forum: Desktop Environments
---

### Post by conor on 2005-12-06
I had just configured my panel to perfection.  I had all the icons arranged the way I wanted them.  I was toying around in firefox when my computer froze.  I thought "No problem" and I hit ctrl-alt-Backspace to exit the gui.  Then I restarted my computer.  When I logged back in I got an error message saying "a panel is already running. I will now quit".  The panel shows up but it will not "unhide" and there are no icons on it.  I tried sudo killall gnome-panel and usually I can get the panel to die.  Then I am left with no panel.  If I hit sudo gnome-panel I can get the original ubuntu panel to pop up and I can work from there.  But when I log off and restart I get the same problem.  I notice in the splash screen that the panel is starting (or rather trying to start) three times.  What can I do to fix this?

---

### Post by aysiu on 2005-12-06
How about without sudo? Just plain old ```
killall gnome-panel
```

---

