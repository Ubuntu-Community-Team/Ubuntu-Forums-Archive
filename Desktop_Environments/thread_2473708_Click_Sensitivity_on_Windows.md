---
title: "Click Sensitivity on Windows"
date: 2022-04-11
forum: Desktop Environments
---

### Post by bugenhagen2014 on 2022-04-11
I just installed Lubuntu and I'm more than happy with it. One thing I have noticed with the LXDE desktop, click points such as expand, collapse, etc. have such a small hot spot, you can spend minutes find it. I've gone back to hotkeying commands.
Is there some kind of simple fix for this?

Thanks,

---

### Post by guiverc on 2022-04-11
You'll have to provide some release details.

Lubuntu doesn't use the LXDE desktop; it's been using the LXQt desktop since Lubuntu 18.10, which means all *supported* releases of Lubuntu use LXQt, not the *deprecated* LXDE desktop used by earlier releases.

*Optional history:  The LXDE devs started porting LXDE from GTK2 to GTK3 & discovered how much heavier it was, and thus blogged about it.. Then then created a new port that used Qt5 instead & found it much lighter & faster (again blogged about), thus the decision to joint with Razor-Qt team and create a replacement desktop called LXQt that remained the L=Light from LXDE & replaced both LXDE & Razor-Qt.  FYI: the blogs I'm talking about were made by PCMan, the creator of `pcmanfm` used by LXDE as file-manager & desktop handler, and it's replacement `pcmanfm-qt` used in LXQt.*

---

