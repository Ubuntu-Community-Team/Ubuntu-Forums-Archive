---
title: "Ubuntu 12.10 extremely slow unity"
date: 2013-03-09
forum: Desktop Environments
---

### Post by Nektarios80 on 2013-03-09
Hi,

I have some serious performance issues with unity. I use the ATI Proprietary driver from the fglrx official repository of ubuntu. 

1) Moving windows about is sometimes smooth but after a while it gets very jerky almost to the point of being unusable. 
2) Some other effects are extremely slow, for instance the "expo" effect when I click on firefox and unity exposes all firefox windows runs at 2-3 PFS.
3) Scrolling on firefox/chromium and other applications is jerky and slow. With the radeon open source driver scrolling was flawless (60 fps constant) with no delay.
4) Also another issuethat annoys me way too much is that the mouse cursor lags also, which baffles me because it is supposed to be a hardware cursor that by definition never lags.

I can't use the radeon open source for it has it's own problems and bugs. It also goes extremely slow (2-3 FPS) when I enable both monitors at full resolution.

Can someone help me out to fix those issues?

System: core i7 920 no overclock
RAM: 6GB
Graphics Card: ATI Radeon HD 5870
Monitors: 30" 2560x1600 & 22" 1920x1080
OS: Ubuntu 12.10 fully updated
uname -a: Linux NekHomeWorkstation 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```
 nektarios@NekHomeWorkstation:~$ fglrxinfo 
display: :1  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string: 4.2.11903 Compatibility Profile Context

```

```
nektarios@NekHomeWorkstation:~$ glxgears 
1235 frames in 5.0 seconds = 246.990 FPS
1291 frames in 5.0 seconds = 257.586 FPS
1230 frames in 5.0 seconds = 245.995 FPS
1287 frames in 5.0 seconds = 257.044 FPS
1139 frames in 5.0 seconds = 227.258 FPS

```

---

### Post by Frogs Hair on 2013-03-09
There are driver PPAs inked in the following page that you may want to look into . [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by fiodev on 2013-03-09
try opening gedit go to preferences go to plugins and deselect the file manager plugin. let me know if your performance gets better after.

---

