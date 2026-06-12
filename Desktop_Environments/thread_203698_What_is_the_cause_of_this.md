---
title: "What is the cause of this?"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Cyraxzz on 2006-06-25
If i restart the X server...

```
Ctrl + Alt + Backspace
```

Then it really increases the speed, so much so I can feel it, i would say it's about 20% faster, all programs start faster, the main computer preformance is faster.

---

### Post by az on 2006-06-25
[QUOTE=Cyraxzz]If i restart the X server...

```
Ctrl + Alt + Backspace
```

Then it really increases the speed, so much so I can feel it, i would say it's about 20% faster, all programs start faster, the main computer preformance is faster.[/QUOTE]
When you start an app, the shared libraries get loaded into memory.  If you reboot, the memory is cleared.  If you just restart the Xserver, the memory is not cleard and when you start the application again, it starts faster because the shared libs are already in place.

---

### Post by mbooth9517 on 2006-06-25
Just to reiterate:.. A common practice with computers is to put into ram: recently written bytes, and recently accessed bytes (from the harddisk). When restarting X, most programs have been recently loaded (i.e recently accessed) hence can be loaded directly from RAM, rather than the hard disk, which is significantly faster than loading them from the harddisk.
If you use your computer a lot since first starting it however, these programs won't be "recently accessed", and hence not kept in RAM, and you'll find it takes about the same time to start X as it would from a cold boot (booting up from scratch)

Martin

---

