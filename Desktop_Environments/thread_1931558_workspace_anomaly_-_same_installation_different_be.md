---
title: "workspace anomaly - same installation different behaviour"
date: 2012-02-25
forum: Desktop Environments
---

### Post by drmtiede on 2012-02-25
I installed Ubuntu 11.10 via wubi on two laptops the same day. in one (called A) everything worked out perfectly, workspaces working like described in description (i.e. drag and drop of windows from one workspace to the other.
On the other laptop (called B) I had some freezes after the first updates - so I reinstalled Ubuntu several times over via wubi. After the first time, when workspaces worked like above, the workspace shows a different behaviour, no drag and drop is possible.

Differences:
A: four workspaces view - drag and drop, workspace shows smaller actual desktop with overlapping or hidden windows, click opens chosen workspace
B: four workspaces view - no drag and drop, windows showed one next to another separated from another with little gray title in the center of each window; click opens "preview desktop", little less than fullscreen, windows visible, no icons, still no draganddrop, second click opens the chosen desktop.
A: dashboard has on the lower end "folded"icons, threedimensionally tilted icontiles, open to full view when pointed on
B: dashboard has fading icons on the lower end, scrolls them to view with scrollwheel.

- I checked I was in Ubuntu and not only Ubuntu 2D in both A and B
- I installed compiz in B, tried around and uninstalled it again, it not being installed on A (and not having solved anything)
- I checked the installed Unity-packs with synaptic and made sure they were the same in A and B, reinstalled the packs again

Any ideas?

---

### Post by drmtiede on 2012-10-16
updated ubuntu and the nvidia optimus drivers (seemd to be the problem) and everything worked fine

---

