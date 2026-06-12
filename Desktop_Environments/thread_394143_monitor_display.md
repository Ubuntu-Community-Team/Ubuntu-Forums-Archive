---
title: "monitor display"
date: 2007-03-26
forum: Desktop Environments
---

### Post by posterart on 2007-03-26
My nvidia GE Force 7300 GT  is listed in the hardware compatible list as detected. I downloaded Feisty 7 and have 1024x768 only for display. The monitor is SyncMaster 940 on 1440x900. How do I get the screen off of low settings? 
With the monitor troubles I have run Feisty as a live cd only, where is my GE Force listed in the control panel? If I load Ubuntu it will be to a 2nd sata drive, XP on sata one. I have no need for the 3D thing, XP and the G5 handle that quite well, just good screen rez. :popcorn:

---

### Post by panurge77 on 2007-03-27
Install nvidia-glx
```
sudo apt-get install nvidia-glx
```

Run in terminal
```
nvidia-settings
```

Change the res...

But you prolly can do this from livecd. Install it before.

---

