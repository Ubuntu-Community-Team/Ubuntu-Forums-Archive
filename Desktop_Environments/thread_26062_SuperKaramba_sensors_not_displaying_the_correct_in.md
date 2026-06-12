---
title: "SuperKaramba sensors not displaying the correct info."
date: 2005-04-11
forum: Desktop Environments
---

### Post by Syrinx on 2005-04-11
I am running the UberMon v0.1 theme for SuperKaramba, and there's a couple parts that are not working.

The first one is for the amount of RAM that I have.  The code for that is:

```
text x=50 y=127 value="RAM:" color=255,255,255 fontsize=14 font="Skia"
text x=90 y=127 sensor=memory format="%um MB" color=255,255,0 fontsize=14 font="Skia"
```

The amount of RAM that I actually have is 1024MB.  The sensor is only reading 354MB!  It's not locking up or running slow, but I would like to figure out why the sensor is picking up the wrong info.

The other is for the space left in my Home directory.  The code for that is:

```
text x=50 y=177 value="Syrinx" color=255,255,255 fontsize=14 font="Skia"
text x=103 y=177 sensor=disk mountpoint="/home" format="%u MB / %up%" color=255,255,0 fontsize=14 font="Skia" interval=60000
```

Here, the issue is that I can't get it to pick up the home directory at all.  I've tried /home, /home/syrinx, and even /syrinx, and nothing works.  The root directory (/) sensor is working, and even the one for my mounted Fat32 drive (/media/realm).  

Any ideas?

---

### Post by Xian on 2005-04-11
[QUOTE=Syrinx]Here, the issue is that I can't get it to pick up the home directory at all.  I've tried /home, /home/syrinx, and even /syrinx, and nothing works.  The root directory (/) sensor is working, and even the one for my mounted Fat32 drive (/media/realm).[/QUOTE]
Is your /home directory actually listed as a mountpoint in your fstab?
It needs to be on a distinct partition.

---

