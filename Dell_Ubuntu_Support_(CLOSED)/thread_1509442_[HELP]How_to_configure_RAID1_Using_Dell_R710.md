---
title: "[HELP]How to configure RAID1 Using Dell R710"
date: 2010-06-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sangprabv on 2010-06-14
Hi,
I just bought a brand new Dell R710 with 2 SAS HDD and hardware RAID controller. We installed it with Lucid 10.04 64bit Server Edition. In the RAID configuration menu we see that it has already configured to RAID1. We tried to turn off the server and pull out HDD A and replace it with HDD B. When we try to boot, it failed and kernel show errors. Anybody can help me to solve this problem? Many thanks for any reply.

---

### Post by dentaro16 on 2010-06-18
have you tired to press CTRL+I when you are booting to get into the PERC controller? you will have to let it rebuild or select the option to rebuild before you boot

---

