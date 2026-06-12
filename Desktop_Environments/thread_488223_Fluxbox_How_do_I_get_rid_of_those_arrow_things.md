---
title: "Fluxbox: How do I get rid of those arrow things?"
date: 2007-06-29
forum: Desktop Environments
---

### Post by oldcpu on 2007-06-29
Those arrow things that cycles through my workspace and application buttons, how do I get rid of them?

---

### Post by yabbadabbadont on 2007-06-29
Edit your ~/.fluxbox/init file and look for a line like this:
```
session.screen0.toolbar.tools:  workspacename, prevworkspace, nextworkspace, iconbar, systemtray, prevwindow, nextwindow, clock
```
Remove the prevworkspace, nextworkspace, prevwindow, and nextwindow keywords.  Save your changes and restart fluxbox.

---

### Post by Nythain on 2007-06-30
sweet, thanks for the info, was wondering the same thing myself, but never really cared to much to find the answer

---

