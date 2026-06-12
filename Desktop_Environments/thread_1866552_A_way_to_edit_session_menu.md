---
title: "A way to edit session menu"
date: 2011-10-21
forum: Desktop Environments
---

### Post by mikesmithv on 2011-10-21
The "session menu" (right-most menu in Unity) has a Webcam menu item which I would like to direct to launch my favorite webcam software.  How do you edit that menu?  It is hard-wired to install Cheese which is not my favorite webcam software (I prefer wxCam for the motion activated feature).

---

### Post by crdlb on 2011-10-21
I just checked, it is [hardcoded into indicator-session]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/oneiric/indicator-session/oneiric/view/head:/src/device-menu-mgr.c#L492"). The easiest option would be to make a symlink, but that's very ugly. The only other option I see is to edit the source and recompile it :/

---

### Post by mikesmithv on 2011-10-21
> **crdlb said:**
> I just checked, it is [hardcoded into indicator-session]("http://bazaar.launchpad.net/~ubuntu-branches/ubuntu/oneiric/indicator-session/oneiric/view/head:/src/device-menu-mgr.c#L492"). The easiest option would be to make a symlink, but that's very ugly. The only other option I see is to edit the source and recompile it :/Thanks for looking into that.  I guess my saying "hard coded" was not an exaggeration!  In a perfect world they would have recycled the "Main Menu" editor code to make that completely configurable but oh well.

---

