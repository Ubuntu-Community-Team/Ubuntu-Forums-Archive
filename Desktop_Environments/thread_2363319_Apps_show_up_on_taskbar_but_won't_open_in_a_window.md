---
title: "Apps show up on taskbar but won't open in a window"
date: 2017-06-08
forum: Desktop Environments
---

### Post by bobnn on 2017-06-08
I'm running ubuntu 14.04.  Once upon a time (at a previous release on this machine), I installed gnome-fallback or gnome-flashback, which ever it was called at the time.  It may have been several upgrades ago.  

At any rate, I have recently turned up an issue where I will open applications, I will get a button for it on the taskbar, but the window never opens, and nothing I do by right-clicking the taskbar button for the app will make it open.

This happens very reliably with bluefish.  The workaround is to copy the launcher to the panel, then modify it's properties from "Application" to "Application in Terminal".

Sometimes it happens to functions inside applications that are supposed to open new windows - same thing, a new item on the taskbar, but no way to get the window to open.

Any suggestions?


PS:  here is what happens when I try to find out what version of gnome-(fallback|flashback) I'm running.

```
[root@dell620:/root ]\# apt-cache policy gnome-flashback
N: Unable to locate package gnome-flashback
[root@dell620:/root ]\# apt-cache policy gnome-fallback
N: Unable to locate package gnome-fallback
[root@dell620:/root ]\# apt-cache search  gnome-flashback
gnome-flashback-desktop - The Gnome Flashback desktop system
gnome-flashback-server - The Gnome Flashback server system
[root@dell620:/root ]\# apt-cache search   gnome-fallback
[root@dell620:/root ]\# apt-cache policy gnome-flashback-desktop
gnome-flashback-desktop:
  Installed: (none)
  Candidate: 1.325-0~eugenesan~trusty12
  Version table:
     1.325-0~eugenesan~trusty12 0
        500 http://ppa.launchpad.net/eugenesan/ppa/ubuntu/ trusty/main amd64 Packages

```

That's some weird stuff there.  I've spent a *lot* of time customizing my environment, so I'm not so sanguine about installing that candidate.

---

