---
title: "Cant get past login"
date: 2008-12-31
forum: Desktop Environments
---

### Post by timjohn7 on 2008-12-31
All of a sudden, after months of stable use of Ubuntu 8.10 (fully updated), I get to the login page and type the first letter of my username.  My system freezes at this point and nothing works.  No Ctrl Alt Fn, no F10, no keyboard response, nothing...
Hard reboot is the only option.  ANy suggestions?
All running on Fujitsu Siemens Amilo P4 with 1G RAM and Intel video card which has given problems but which have all been resolved.

---

### Post by prshah on 2008-12-31
> **timjohn7 said:**
> All of a sudden, after months of stable use of Ubuntu 8.10 (fully updated), I get to the login page and type the first letter of my username.  My system freezes at this point and nothing works.  No Ctrl Alt Fn, no F10, no keyboard response, nothing.

Is your HDD activity indicator constantly (not flickering) lit?

Boot into recovery mode, then give the commands```
touch /forcefsck
reboot
``` This will trigger a diskcheck.

Post back with results (or lack / questions thereof)

---

### Post by timjohn7 on 2008-12-31
Hi PRShah
Apologies for taking a while to get back to you. I have got  a black screen but can chnge ttys and login.
I have just rebooted and have the same problem as before.All looked good until I enter the 1st letter of my username... then total freeze.
Also if I try F10 before entering username, I get a ghost image of the menu, but no functionality and I cant see any text in the Session Menu.

---

