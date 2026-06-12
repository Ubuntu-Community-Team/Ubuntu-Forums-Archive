---
title: "ubuntu 20.04 gnome-shell high CPU usage"
date: 2020-05-07
forum: Desktop Environments
---

### Post by andrea70d on 2020-05-07
Hi everyone. Last week i installed **ubuntu 20.04** on hp 250 g7. since yesterday I have the problem, the gnome-shell process takes a lot of cpu.obviously the percentage varies but in general it is high and the PC is almost unusable

   2138 andrea    20   0 4468524 303796 131820 S  **15,6 **  1,2  18:40.43 gnome-shell                 



can someone help me?

---

### Post by CelticWarrior on 2020-05-07
HP 250 g7 has several different hardware configurations and some include Nvidia Graphics. If yours has Nvidia then you should install Nvidia proprietary drivers.

---

### Post by andrea70d on 2020-05-08
how can I do? can you help me?

---

### Post by CelticWarrior on 2020-05-08
Well, open Additional Drivers and check what's offered.

My comment in the other post is just an hypothesis with explanatory power about your reported issue: *the gnome-shell process takes a lot of cpu.obviously the percentage  varies but in general it is high and the PC is almost unusable*. But no more than an hypothesis that begs confirmation: Does it really have Nvidia Graphics? The other option for that model line is plain Intel Graphics and if so, proprietary drivers isn't applicable.

But then you ask what to do?... Well, you should know your hardware before installing an OS, don't you think?

---

### Post by ahaslam on 2020-05-08
Controversial solution: Install plasma. KDE is so much lighter these days.

---

### Post by CelticWarrior on 2020-05-09
> **ahaslam said:**
> Controversial solution: Install plasma. KDE is so much lighter these days.

Undoubtedly it is but if running with nouveau it'll suffer the same problem.
The difference between DEs has to do with RAM mostly.

---

