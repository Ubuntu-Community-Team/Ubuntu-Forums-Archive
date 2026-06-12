---
title: "Power management"
date: 2015-10-01
forum: Desktop Environments
---

### Post by l0uismustdie on 2015-10-01
Hello, I'm looking for some help with power management on my desktop server (Ubuntu 14.04.3 LTS). I would really like to be able to suspend the machine after being idle for some period of time with wake-on-lan enabled but I haven't found a way to issue magic packets from my router.

Recently I tried TLP and enabled disk spin down and some other options. I've also gone into the 'Disk' settings and enabled standby after 20 minutes, APM level 127, and AAM 128. However, it doesn't sound like anything is spinning down.

I'm curious if there is any way to test that these features are working and if anyone has any other ideas about how to put some of the hardware to sleep when the machine isn't being used.

Thanks.

---

### Post by dino99 on 2015-10-02
power management is not well done on linux sadly; from time to time, the kernel propose some improvment but still lack a lot

---

