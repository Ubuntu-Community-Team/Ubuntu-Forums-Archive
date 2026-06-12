---
title: "DMA on 2.6.8.1 kernel"
date: 2006-06-08
forum: Desktop Environments
---

### Post by red_shrike on 2006-06-08
OK guys, I have an advanced question. It is about how to enable DMA support on 2.6.8.1 kernel; problem is how to do it - I have tried recompiling kernel with various options, but nothing works. If anyone is interested I can send config file from Block devices and ATA/IDE/... from kernel setup. Reason I need 2.6.8. kernel is because it is the only kernel, with ? 2.6.9? that allows me to watch movies in full screen and before to use pctel softmodem. I can easily solve problem by using 2.6.12 kernel, but then movies are small screened and if 2.6.8.1 is used, than I can not watch CSS DVD's. My configuration is P2 400 Mhz, 128 Mb RAM 133 Mhz and whole configuration is HP VLi8 series. Anyone?!

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=red_shrike]OK guys, I have an advanced question. It is about how to enable DMA support on 2.6.8.1 kernel; problem is how to do it - I have tried recompiling kernel with various options, but nothing works. If anyone is interested I can send config file from Block devices and ATA/IDE/... from kernel setup. Reason I need 2.6.8. kernel is because it is the only kernel, wUbuntu
 ith ? 2.6.9? that allows me to watch movies in full screen and before to use pctel softmodem. I can easily solve problem by using 2.6.12 kernel, but then movies are small screened and if 2.6.8.1 is used, than I can not watch CSS DVD's. My configuration is P2 400 Mhz, 128 Mb RAM 133 Mhz and whole configuration is HP VLi8 series. Anyone?![/QUOTE]
Why not upgrade to Dapper ? It includes the 2.6.15 kernel so your problem might be fixed. If it is not you can try custom compiling a kernel (2.6.16.20 stable) and it will most likely work.

---

