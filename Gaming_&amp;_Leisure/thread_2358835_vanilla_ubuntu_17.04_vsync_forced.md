---
title: "vanilla ubuntu 17.04 vsync forced"
date: 2017-04-17
forum: Gaming &amp; Leisure
---

### Post by carrionbear on 2017-04-17
i havent been able to find any help for this anywhere else, not through the amdgpu manpages or the arch wiki or anywhere else, so here i am. no matter what i do, i cannot get certain games to go past 60 frames per second although some others do. glxgears, xonotic and l4d2 cannot go past 60, as well as games running under wine like quake live. tomb raider does go past 60, though. im using ubuntu 17.04 with an rx 470 with an fx-6300. ive installed 16.04.2 in a dual boot configuration and it's vsync is not forced, whether using proprietary drivers or not.

this is my 20-amdgpu.conf
```

Section "Device"
    Identifier "AMD"
    Driver "amdgpu"
    Option "DRI" "3"
    Option "EnablePageFlip" "on"
    Option "TearFree" "off"
    Option "ShadowPrimary" "off"
EndSection


```

---

