---
title: "m and s key not working properly after upgrade"
date: 2010-05-04
forum: Desktop Environments
---

### Post by chienyang on 2010-05-04
Hello everyone,

I upgraded two machines to 10.4 TLS.  When I press "s" key, system shutdown menu is displayed, and when I press "m" key, message menu is displayed.  Has anyone else with similar issue?  If you do, how did you resolve it?  Thanks.

---

### Post by artooro on 2010-05-04
I have the same issue, not resolved yet

---

### Post by tnunn2 on 2010-05-04
I am also getting the same problem.  I tried the instruction described here: [https://help.ubuntu.com/community/AppleKeyboard#Ubuntu](https://help.ubuntu.com/community/AppleKeyboard#Ubuntu) to no avail.  

The events when typing the s key is as follows:

FocusOut event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

LeaveNotify event, serial 31, synthetic NO, window 0x3800001,
    root 0x2e, subw 0x3800002, time 1707308009, (34,37), root:(35,88),
    mode NotifyGrab, detail NotifyNonlinearVirtual, same_screen YES,
    focus YES, state 0

FocusOut event, serial 31, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyPointer


Your assistance will be greatly appreciated.

---

### Post by chienyang on 2010-05-04
I just found out this is a known issue.  The bug is file as 568401, and the solution is posted at [https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/568401](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/568401).

---

### Post by tnunn2 on 2010-05-05
Thanks...that worked. For some reason the patch command did not work so I updated tomboykeybinder.c manually.

---

