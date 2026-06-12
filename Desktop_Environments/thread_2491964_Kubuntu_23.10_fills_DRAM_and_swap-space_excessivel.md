---
title: "Kubuntu 23.10 fills DRAM and swap-space excessively, but GNOME is OK"
date: 2023-10-26
forum: Desktop Environments
---

### Post by randy-1 on 2023-10-26
KDE Plasma paralyzes its use by

 excessive DRAM consumption with subsequent unrestrained writing to the swap partition(s)!

 There are 4GB DRAM and 51GB swap space (1Gb on RAID1 partition + 50GB on normal HDD partition as a test):

 in KDE shows "cat /proc/meminfo"

 MemFree 150MB

 MemAvailable 430MB

 The swap memory is initially used with 1.5GB and when changing desktops or starting new programs, it becomes MORE AND MORE FULL; with 10GB of swap the PC still responds (with 1GB of swap space the PC was immediately dead...), but  is of course very slowed down!

 However, with GNOME:

 MemFree 2.2GB

 MemAvailable 2.8GB

 SwapTotal 51GB

 SwapFree 51GB

 The swap memory is not used at all and, as is usually the case with Ubuntu, could also be omitted with 4GB DRAM.  .  .

As a reference:
[https://forum-ubuntuusers-de.translate.goog/topic/kubuntu-23-10-reagiert-wg-extremer-festplatten/?_x_tr_sl=auto&_x_tr_tl=de&_x_tr_hl=de&_x_tr_pto=wapp#post-9400672](https://forum-ubuntuusers-de.translate.goog/topic/kubuntu-23-10-reagiert-wg-extremer-festplatten/?_x_tr_sl=auto&_x_tr_tl=de&_x_tr_hl=de&_x_tr_pto=wapp#post-9400672)

---

### Post by randy-1 on 2023-10-26
Kubuntu can't use widgets with my setup(i915-graphics): 

[https://discuss.kde.org/t/kde-plasma-5-27-desktop-freaks-out/6495/3](https://discuss.kde.org/t/kde-plasma-5-27-desktop-freaks-out/6495/3)

---

### Post by Frogs Hair on 2023-11-05
Running the top command  in the terminal may reveal what process is using memory.
```
top
```

---

### Post by randy-1 on 2023-11-06
Thank You for Your reply !

As my system just uses onboard-graphics(i915) and is rather old/obsolete for most users, I don't think, KDE-developers will have a look at this problem !?
For me it's for now OK, not to use KDE-widgets at all . . .
May be it's a matter interest for someone, to find out the reason for this strange behaviour ?

---

