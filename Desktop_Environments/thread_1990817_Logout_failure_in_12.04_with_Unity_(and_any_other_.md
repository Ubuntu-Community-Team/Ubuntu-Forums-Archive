---
title: "Logout failure in 12.04 with Unity (and any other DE)"
date: 2012-05-29
forum: Desktop Environments
---

### Post by blinxwang on 2012-05-29
When I log out from the menu, nothing (on-screen at least) happens and I have to either shut down the computer or restart it. I have the latest updates and am on a 64-bit Ubuntu with Kernel 3.2.0-25 (proposed). Would that be the problem?
Graphics card is Radeon HD 6970; this problem happens with both FGLRX and Gallium3D drivers.

---

### Post by siepo on 2012-05-30
Maybe bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1004983]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1004983") applies.

As a workaround, instead of logging out the regular way you could try to switch to a virtual terminal (Control_Alt-F2), log in there and close down your computer with
```
sudo halt
```

---

### Post by blinxwang on 2012-06-02
> **siepo said:**
> Maybe bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1004983]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1004983") applies.

As a workaround, instead of logging out the regular way you could try to switch to a virtual terminal (Control_Alt-F2), log in there and close down your computer with
```
sudo halt
```

Ah, I see. Worked for me. Thanks!

---

