---
title: "[SOLVED] missing title and window borders with Compiz Fusion"
date: 2007-10-27
forum: Desktop Environments
---

### Post by caffienefree on 2007-10-27
EDIT: *bangs head* Why did I put this in the wrong forum? Could a moderator please delete?

---

### Post by StevenHarper on 2007-10-27
Im not sure but on Nvidia you have to have

```
Section "Device"
...
...
...
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
EndSection
```


also this can help with intel
```

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

I do remember that I moved my xorg.conf out of the way post-upgrade on my intel chipset laptop and let the bullet-proof X rebuild it, then compizfusion started working.

good luck

Steve

---

