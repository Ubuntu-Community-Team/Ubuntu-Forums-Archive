---
title: "Free RAM in top and gnome-system-monitor mismatch"
date: 2009-04-13
forum: General Help
---

### Post by smani on 2009-04-13
Just noticed, top reports
3880984k total,  1422060k used,  2458924k free,
while gnome-system-monitor reports 514 MiB out of 3.7 GiB used. What is going on?!
Indeed, in some situations (mainly after running a wine application) top says as little as 20'000 KiB of memory are free, and indeed the system lags like hell with the harddisk constantly working, but also in those situations gnome-system-monitor says that maybe 1GiB are used. What is funny is that the sum of used memory of the processes listed in top is far less then the memory he reports used (actually it is more like the amount used reported by gnome-system-memory).
I attached two screenshots showing the situation. Anyone can tell me what's up?
Thanks!
smani

---

### Post by skymera on 2009-04-13
top reports system usage + cached + buffers.

do free -m to see memory statistics

---

### Post by smani on 2009-04-15
Thanks for your reply. I also found the cause of the lags: preload.

---

