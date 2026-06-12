---
title: "swap not getting utilized"
date: 2009-04-01
forum: General Help
---

### Post by Voyage'ur on 2009-04-01
em new to ubuntu community. I start now with my question on swap space. It seems swap space is not getting utilized in my machine.

Swap:      1951856          0    1951856

---

### Post by gtrtx on 2009-04-01
How much RAM does the system have?

If you have 1 GB or more, you may rarely see any Swap activity.

---

### Post by perpetualcacophany on 2009-04-01
It is not a problem if your swap is not being utilized all the time. Swap is usually only accessed if your normal RAM is maxed out. The computer then uses your swap partition like RAM in order to keep your system from locking up.

---

### Post by drs305 on 2009-04-01
The previous posters are correct and I'll add if your swap is corrupted the values usually will all be 0 > ( 0 0 0 ). Your swap just isn't needed at present.

---

### Post by Voyage'ur on 2009-04-01
cat /proc/meminfo
MemTotal:      2066084 kB
MemFree:       1301184 kB
Buffers:         36932 kB
Cached:         366480 kB
SwapCached:          0 kB
Active:         392860 kB
Inactive:       209192 kB
HighTotal:     1169924 kB
HighFree:       595980 kB
LowTotal:       896160 kB
LowFree:        705204 kB
SwapTotal:     1951856 kB
SwapFree:      1951856 kB

---

### Post by gtrtx on 2009-04-01
That looks fine.

While it won't hurt anything, you could easily get by with probably a swap partition half that size. Probably much smaller. 

My system has a 1GB swap partition and I rarely see more than 10MB used. Depending on what I'm doing, sometimes it will go days untouched.

---

### Post by Voyage'ur on 2009-04-01
Thanks for the details

---

