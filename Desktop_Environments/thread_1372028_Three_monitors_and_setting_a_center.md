---
title: "Three monitors and setting a center"
date: 2010-01-04
forum: Desktop Environments
---

### Post by rbf on 2010-01-04
I have Ubuntu 9.10 with latest updates installed on a system with two graphics cards (identical nVidia Geforce 280) and have three identical monitors (Samsung SyncMaster T260 - two connected to the first graphics card and one connected to the first port on the second graphics card). 

Everything works fine except I want to change which monitor is the "main" monitor. As of now the left-most monitor has the Gnome task bars on it and the other two monitors are to the right of it (both physically and as far as the desktop goes). What I would rather have is the center monitor be the "main" monitor with the task bars and the left monitor be left of it and the right monitor be right of it. I have googled this to death and tried many different configurations but no matter what the left-most monitor ends up being the "main" screen.

I've had the best luck with using the nvidia-settings tool and enabling xinerama. I've gone through so many xorg.conf's that I'm not sure which one to post...

If that's too many words for some of you, here is a visual representation:
* = main
Currently: Left*   Middle   Right
Desired: Left   Middle*   Right

---

