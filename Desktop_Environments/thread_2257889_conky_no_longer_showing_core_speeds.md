---
title: "conky no longer showing core speeds"
date: 2014-12-23
forum: Desktop Environments
---

### Post by CatKiller on 2014-12-23
My conky used to show the effect of frequency scaling on each core using ${freg_g}. This stopped working a while ago (can't remember exactly when; I suspect a kernel update). I don't appear to be able to change them using the CPU Frequency Scaling Monitor panel widget, either, which used to work. I understand that there were changes made to account for the way that newer Intel processors operated, but it's a bit annoying that it removes functionality from my 2500K. Is there anything that can be dome to give Conky better data, or is there likely to be an update to Conky to take account of the fact that it's being lied to?

EDIT: Potentially relevant; to Governor seems to prefer Performance rather than the Ondemand that was the previous default.

---

### Post by CatKiller on 2014-12-23
Actually, I managed to fix it by purging my cpufrequtils configuration and creating a new one. All is happy now.

---

