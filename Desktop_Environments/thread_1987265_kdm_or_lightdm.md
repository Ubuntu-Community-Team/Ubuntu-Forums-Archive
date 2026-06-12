---
title: "kdm or lightdm"
date: 2012-05-26
forum: Desktop Environments
---

### Post by Brizlitman on 2012-05-26
i just installed kde in precise and i'm finding it hard to choose between kdm and lightdm.

---

### Post by zombifier25 on 2012-05-26
LightDM is "lighter" since LightDM does not load any libraries at startup, unlike GDM which loads GNOME libs, and KDM which loads KDE libs.

---

### Post by osirisgothra on 2013-02-20
> **zombifier25 said:**
> LightDM is "lighter" since LightDM does not load any libraries at startup, unlike GDM which loads GNOME libs, and KDM which loads KDE libs.

i guess the question would be, does running kdm before launching kde benefit because it uses some of the same libraries or are they released and then reloaded again prior to starting kde (aside from the disk cache optimizations that would happen since the data was recently accessed it would be a cache hit if it hadn't been unallocated yet)

---

### Post by aarons6 on 2013-02-20
no, and the newer kubuntu uses lightdm as default.

---

### Post by doctor82 on 2014-02-20
Thanks. (I guess there should be a thanks button in the forum to save space.)

---

### Post by soum_axetuirk on 2014-02-20
Best use LightDM

---

### Post by Mr_Bumpy on 2014-02-21
KDM is better if you have multiple monitors, because LightDM will splat your login box between the screens (half on one monitor, half on the other).

---

### Post by undecidable on 2014-07-13
Kubuntu 14.04:  lightdm gives me a duplicated login box, 1 on each screen.  just fine.

---

