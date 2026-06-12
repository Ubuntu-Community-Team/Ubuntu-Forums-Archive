---
title: "Desktop System Monitors"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by RAB314 on 2007-04-06
Im using gdesklet. The network monitor is working  but i get no reading on my HDD Temp and CPU temps anyone know what could keep it from reading that info??

---

### Post by yabbadabbadont on 2007-04-06
For hdd temps, you probably need to install, wait for it...  hddtemp.  ;)

For CPU temps, you need to make sure that the correct module(s) are loaded for your motherboard.  I had to add a module to /etc/modules to get mine to show up.  Or you may need to install and configure the lm_sensors package.

---

