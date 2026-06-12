---
title: "Ubuntu 6.06 - No digital sound on Gigabyte GA-8IK1100 motherboard"
date: 2008-04-03
forum: Desktop Environments
---

### Post by warp99 on 2008-04-03
Did you try to run the audio channel to AC3 pass-through in Totem (Xine)?  You have the levels in alsamixer on the IEC958 channel turned all the way up? Also what version of alsa are you using?

```
sudo apt-cache show alsa-base
```

Also run a 

```
lspci -v |grep audio
```

 and post the results here.

---

