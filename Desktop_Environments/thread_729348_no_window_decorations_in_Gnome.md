---
title: "no window decorations in Gnome"
date: 2008-03-19
forum: Desktop Environments
---

### Post by jphilips on 2008-03-19
This is on Hardy Heron with the latest upgrades. In my own account, everything looks fine. But my wife and daughter have non-sudo accounts. If I log in to their accounts, programs have no window decorations and you can't move them. I tried deleting any Gnome-related config files and regernating them. But this was no help. Any ideas on what would get their accounts back to normal?

---

### Post by prefec2 on 2008-03-24
First I would create a new account for testing purposes with the same privileges as the failing accounts. Then log in to this new account and check if the same problem occurs.

Possible causes for the problem:
a) You changed something with the DRI stuff in xorg.conf
b) In gutsy compiz was used for effects, now some of these effects can be produced by metacity.
So one possible test is to switch these effects off in System/Preferences/Appearance. 
c) One problem could be that compiz or parts of it have been removed. 
d) metacity is set to use the composite extension but is not able to use it because compiz is running.

The metacity effects can be turned on and off with gconf-editor only.

Hope that helps
  Reiner

---

### Post by Therion on 2008-03-24
Log into their account's, start the Compiz Settings Manager and enable the "Window Decorations" plugin.

If still no joy:```
metacity --replace
```

---

### Post by crocowhile on 2008-03-24
I had a similar program. I solved using emerald
emerald --replace &

---

