---
title: "workspaces: 'next/prev' vs 'right/left'?"
date: 2013-08-15
forum: Desktop Environments
---

### Post by chris_varner on 2013-08-15
Is there a way to move to the next workspace, rather than right/left/up/down? In other words, I want to cycle through my workspaces regardless of their notional geometry.. As a workaround, I changed from a 2x2 grid to a 1x4 which would be fine, but if I move 'right' from my last workspace, I would like to go to my first workspace (ie, I'd like a circular list of workspaces).

I'm using 12.04/Unity on a desktop. Thanks!

---

### Post by deadflowr on 2013-08-15
I'm guessing you have compizconfig-settings-manager installed.
If so, then go to desktop wall, then veiwport switching and enable allow wrap around.

If you don't have ccsm installed, then install it.

---

### Post by markbl on 2013-08-15
You may prefer the dynamic workspaces used in gnome-shell? I  and many others do.

```
apt-get install gnome-shell
```

Then log out of Ubuntu session (i.e. Unity) and log in with GNOME (i.e. gnome-shell). They coexist without issue.

---

