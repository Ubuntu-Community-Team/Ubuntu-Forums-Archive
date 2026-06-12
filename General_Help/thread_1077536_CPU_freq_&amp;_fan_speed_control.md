---
title: "CPU freq &amp; fan speed control"
date: 2009-02-22
forum: General Help
---

### Post by panaut0lordv on 2009-02-22
My problem is when I play video games system crashes due to the overheat. My nvidia-settings shows "62 C" so it's not the problem and CPU is cool too.
I'm supposing my chipset is overheating so question now:

How can I set power management in ubuntu to:
a) disable it completely so BIOS will control fans & CPU speed
OR
b) turn it to be as fast as they can (especially fans)

---

### Post by FAMUgolfer on 2009-02-22
I'm having the same problem with an acer 4530-5889, nvidia 9100m, dual-booting xp and 8.10.  My temps are around 60-70C constantly even when idle with no programs running except cairo-dock and compiz. This causes my fan to constantly be blowing hot air since my cpu frequency is always maxed at 1.91Ghz.

If there is a way for BIOS to control cpu frequency, i'm sure this problem will be resolved.

Any suggestions???

And yes I've cleaned out the fan for dust.

---

### Post by eldragon on 2009-02-22
> **FAMUgolfer said:**
> I'm having the same problem with an acer 4530-5889, nvidia 9100m, dual-booting xp and 8.10.  My temps are around 60-70C constantly even when idle with no programs running except cairo-dock and compiz. This causes my fan to constantly be blowing hot air since my cpu frequency is always maxed at 1.91Ghz.

If there is a way for BIOS to control cpu frequency, i'm sure this problem will be resolved.

Any suggestions???

And yes I've cleaned out the fan for dust.

what cpu do you have? your cpu scaling governor seems to be broken? do you boot with noacpi, nolapic or something of the sort? this could be it.

---

### Post by panaut0lordv on 2009-02-22
Hey, and my question? :|

---

### Post by eldragon on 2009-02-22
> **panaut0lordv said:**
> Hey, and my question? :|

i was actually asking you


EDIT
uhh, i read both posts...damn me for not reading usernames... i somehow thought it was all the same person,

EDIT 2:

i dont know how to make the bios control the cpu fan. but if your fan can be controlled, there should be something here:
```

/proc/acpi/fan

```

allowing you to control the fan speed. there are daemons in charge of that too, but since i dont have 1 single station with fan control thingies, i cannot verify this.

---

### Post by FAMUgolfer on 2009-02-23
/proc/acpi/fan

This file is empty. What should be in this file??

---

