---
title: "D620 - Hardy - Screen Resolution Problem"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by walterhtx on 2008-06-27
Hardy was running really well for me on my D620, then I applied a huge round of Ubuntu updates (a week or two ago) which seem to have messed messed up the OS's ability to correctly detect the laptop's LCD.

Video chipset is NVidia Quadro NVS110M
Native LCD resolution is 1440 X 900

Highest available setting is now 1024 X 768. Has anyone else been hit by this? If so, is there a fix for it? Any help would be much appreciated!

---

### Post by walterhtx on 2008-06-27
> **walterhtx said:**
> Hardy was running really well for me on my D620, then I applied a huge round of Ubuntu updates (a week or two ago) which seem to have messed messed up the OS's ability to correctly detect the laptop's LCD.

Video chipset is NVidia Quadro NVS110M
Native LCD resolution is 1440 X 900

Highest available setting is now 1024 X 768. Has anyone else been hit by this? If so, is there a fix for it? Any help would be much appreciated!

I have reinstalled Hardy and applied all 205 O/S updates on my D620 and once again the display is beautiful at the correct resolution (1440 X 900).

I suspect that, since I was using the restricted NVidia driver (instead of the native driver), some download along the way broke the driver. So, with that in mind, I didn't enable the restricted driver until after I had reinstalled 8.04 and applied all O/S updates. Worked like a charm.

Obviously this isn't a solution, but hopefully someone can avoid the same pitfall. Take care!

---

