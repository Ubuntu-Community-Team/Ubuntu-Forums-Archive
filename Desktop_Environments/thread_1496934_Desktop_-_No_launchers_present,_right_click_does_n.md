---
title: "Desktop - No launchers present, right click does nothing?"
date: 2010-05-29
forum: Desktop Environments
---

### Post by ub-newbie on 2010-05-29
OS: Lucid

Symptoms:  Launchers are in Desktop folder, but they are not on the desktop.  Also, when I "right click" on desktop, nothing happens (no pop up menus). Attempts to add new launchers to desktop (via "add launcher to desktop" or "click-n-drag") are not successful.  Symptoms the same on both monitors.

Possible Cause:  I just completed a problematic install of 2nd monitor (NVidia X Server).  Currently running in TwinView.  After install was completed I noticed launchers were missing.

Info:  Desktop folder is owned (RW) & group (R) to my user, execute is enabled, and Others is R, as are all files in folder.

I'm not sure where to start troubleshooting?

---

### Post by ub-newbie on 2010-05-30
Ok, Found another post here "RC Frozen desktop. Can't right-click"..

It said to go into xorg.conf, under "Screen" and add ```
OPTION "AddARGBGLSVisuals" "True"
```
So I did, and things are back to the way they should be.

Looks like a problem with the NVidia Server.  Now that I look back at my previous version of Xorg.conf I see that this option was in that file.

So, Issue is resolved.

---

