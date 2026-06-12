---
title: "Ubuntu random Freeze with Minecraft"
date: 2013-12-01
forum: Desktop Environments
---

### Post by Teethdude on 2013-12-01
After many attemps to find the error code, I did this time after it froze and it let me switch to a virtual console. I found the error/system messages below:
```
mike-Compaq kernel: [24456.923918] [drm:i915_hangcheck_elapsed] *ERROR* stuck on render ringDec  1 10:24:22 mike-Compaq kernel: [24456.932054] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x3d5a000 ctx 1) at 0x3d5a1d8
```
PS:  I hope I put this in the right location.

[ATTACH=CONFIG]248227[/ATTACH][ATTACH=CONFIG]248228[/ATTACH][ATTACH=CONFIG]248229[/ATTACH]

---

### Post by sanderj on 2013-12-01
And ... did you google "[drm:i915_set_reset_status] *ERROR* render ring hung inside bo"  ?

---

### Post by Teethdude on 2013-12-01
It seems to be a Graphics hang. Could you elaborate it a bit please?

---

### Post by edd07 on 2013-12-24
I'm running into this bug as well when trying to play Minecraft.  I'm on a Dell Vostro with a Core i5-2410M and 64-bit Ubuntu 13.10 (Saucy).

The details page of system setting tells me my graphics driver is "Intel Sandybridge Mobile"

Thanks in advance

---

