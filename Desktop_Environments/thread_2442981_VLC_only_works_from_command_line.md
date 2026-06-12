---
title: "VLC only works from command line"
date: 2020-05-09
forum: Desktop Environments
---

### Post by johnzbesko on 2020-05-09
Performed fresh install of Kubuntu 20.04.  When I right-click on a video to play with vlc, vlc crashes/doesn't play. If I invoke vlc from the command line, it does work and will play a selected file. I remember this happened a long time ago (18.04?) so I tried uninstalling vlc and re-installing using snap. I also tried to disable apparmour (didn't help) and tried disabling vlc as an individual program from apparmour. Still no luck. What is going on???

---

### Post by johnzbesko on 2020-05-10
OK, so now I've discovered that the chromium browser will no longer work at all. From the command line, I get:

$ chromium
snap-confine has elevated permissions and is not confined but should be. Refusing to continue to avoid permission escalation attacks: Operation not permitted

This happened after I removed and re-installed chromium and apparmor. Aaargh!

---

### Post by johnzbesko on 2020-05-10
Uninstalling snap, apparmor, and chromium fixed the problem with the chromium browser not working. However, the vlc issue is still active. Also, vlc does not run when invoked from the KDE start menu.

---

