---
title: "Xubuntu with 3 workspaces - how to keep new windows in the same workspace"
date: 2015-07-16
forum: Desktop Environments
---

### Post by majest2 on 2015-07-16
I am on on Xubuntu 14.04 and have 3 workspaces.

I would like to basically have it so these seem like 3 independent computers, so that all windows relating to processes on workspace "1" will open only in that workspace. Unfortunately, as it is now, I set up something to run in workspace 1 (e.g. a Matlab script) but it displays new windows (from Matlab) wherever I currently am, which could be workspace 2 where I'm writing a document.

So there is really no separation between the workspaces - after a while, all the windows are spread out over every workspace. How can I keep them contained? Thanks :)

---

### Post by Toz on 2015-07-16
Try setting the window raise action to do nothing:
Settings Manager >> Window Manager Tweaks >> Focus tab >> "When a window raises itself" = "Do nothing"

This way, when matlab displays a new window, it will stay on the workspace that matlab is on and not raise itself on your current workspace.

---

### Post by majest2 on 2015-07-16
Thanks Toz. That looks like it's the ticket.

---

