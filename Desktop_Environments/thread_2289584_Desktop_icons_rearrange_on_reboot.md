---
title: "Desktop icons rearrange on reboot"
date: 2015-08-05
forum: Desktop Environments
---

### Post by majest2 on 2015-08-05
There's a kind-of annoying bug in Xubuntu 14.04 where the icons rearrange themselves when you reboot. I've seen it posted in other places and the workaround is not very appealing (basically make desktop read only / immutable by running a script and if you ever want to add or change anything, undo it then reapply it). This is pre windows 3.1 sophistication.... there must be a proper fix?! Does anyone know what to do? I recompiled xfce4-power-manager once, so I can probably handle recompiling if it's necessary.

[http://ubuntuforums.org/showthread.php?t=2095588](http://ubuntuforums.org/showthread.php?t=2095588)

[URL="https://forum.xfce.org/viewtopic.php?id=7597"]https://forum.xfce.org/viewtopic.php?id=7597
[/URL]
[https://bugzilla.xfce.org/show_bug.cgi?id=12098](https://bugzilla.xfce.org/show_bug.cgi?id=12098)

---

### Post by Toz on 2015-08-05
[Work]("https://bugzilla.xfce.org/show_bug.cgi?id=11266") is currently on-going to address this bug. There have been some fixes added to the git tree post 4.12 release, but there are still some instances (as noted in the bug report) where icon positions reset.

---

