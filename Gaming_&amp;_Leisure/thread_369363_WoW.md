---
title: "WoW"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by ninjachicken on 2007-02-24
I can log into wow on x1300 radeon but before my char loads it locks up is there any thing i can do to fix this?

---

### Post by Sammi on 2007-02-24
From the [community WoW/Wine howto]("https://help.ubuntu.com/community/WorldofWarcraft"):
> For users with an ATI video card: certain cards have trouble rendering games and video in opengl using current flgrx drivers which will cause your computer to hard locks when you attempt to enter a domain. This error will occur just after character creation/selection, as the game environment is loading, or possibly after a short period of play. In order to fix this error, add the following lines of code to your xorg.conf file in the ATI device section:
```
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
```

---

### Post by hikaricore on 2007-02-24
Just FYI ninjachicken, please only make one topic for help per subject matter.  You've posted the same question about 4 times from what I've seen since just yesterday.  This will not benefit you in the long run.

---

