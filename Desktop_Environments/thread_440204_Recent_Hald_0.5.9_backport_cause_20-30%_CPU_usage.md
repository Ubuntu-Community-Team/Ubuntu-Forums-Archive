---
title: "Recent Hald 0.5.9 backport cause 20-30% CPU usage"
date: 2007-05-11
forum: Desktop Environments
---

### Post by shizeon on 2007-05-11
Hello,
  The backport repository just released hal 0.5.9 for feisty.  After install, the hald process consumes about 20-40% of my CPU constantly.  I just downgraded each of the following packages back to the official version and the problem goes away.   Anyone else see this?

hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Thanks

---

