---
title: "The composite extension is not available (yes I searched, different problem than most"
date: 2007-11-28
forum: Desktop Environments
---

### Post by elementboarder2 on 2007-11-28
I get this when I try to enable desktop effects.  I searched, and most people said it was a problem with the xorg.conf file.  So I tried to change the 

Section "Extensions"
    Option         "Composite" "Disabled"
EndSection

to

Section "Extensions"
    Option         "Composite" "Enabled"
EndSection

But I still get the same error.  Anyone know whats up?  I am using an ATI Radeon Mobile X200, with fglrx.

---

### Post by chronic on 2007-11-29
what gfx card do you have?

---

### Post by eye208 on 2007-11-29
> **elementboarder2 said:**
> But I still get the same error.  Anyone know whats up?  I am using an ATI Radeon Mobile X200, with fglrx.
The version of fglrx that is currently in the repos does not yet have the composite extension. If you try to enable it through xorg.conf, you'll only make things worse because you'll lose direct rendering.

If you really need desktop effects, there are two workarounds: Either install XGL (an X.org replacement) or use the latest version of fglrx (from the ATI/AMD website) which is supposed to have the composite extension (aka. AIGLX support).

---

### Post by elementboarder2 on 2007-11-29
> **eye208 said:**
> The version of fglrx that is currently in the repos does not yet have the composite extension. If you try to enable it through xorg.conf, you'll only make things worse because you'll lose direct rendering.

If you really need desktop effects, there are two workarounds: Either install XGL (an X.org replacement) or use the latest version of fglrx (from the ATI/AMD website) which is supposed to have the composite extension (aka. AIGLX support).

Thanks, but now it just says "desktop effects could not be enabled"

---

### Post by eye208 on 2007-11-30
Please check the output of
```
glxinfo | grep "direct rendering"
```

Does it say Yes or No?

---

