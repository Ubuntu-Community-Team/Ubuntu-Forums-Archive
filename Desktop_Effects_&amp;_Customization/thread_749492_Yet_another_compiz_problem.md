---
title: "Yet another compiz problem"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by thescientist213 on 2008-04-08
Hello, sorry if this is posted somewhere I've looked around for a while trying to figure it out but no luck.

I'm trying to get Compiz-Fusion to work I've got a NVIDIA GeForce6600 and I'm using this guide [http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)
I do have restricted drivers enabled and everything is completed updated.

Basically what happens is, when i click the "custom" option under Appearance it lets me click it and no errors come up or anything, however it doesn't stick. When i close appearance compiz still doesn't work. I went back into appearance and "custom" isn't selected anymore. It's back on whatever setting it was on before. I followed that guide very carefully and this is a fresh install. If you need any more info let me know and thanks for the help.


Also here's what comes up in terminal when I type "compiz"
```
vid@david-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0140 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Edit: Just noticed Xgl is not present I'll get that and see if it fixes it.

---

### Post by thescientist213 on 2008-04-08
I activated XGL and now it says NVIDIA not present. Still the same problem though.

---

### Post by thescientist213 on 2008-04-08
I dunno what i did but i fixed it. Sorry for the bother.

---

