---
title: "banshee problem"
date: 2009-12-24
forum: Desktop Environments
---

### Post by phillychease on 2009-12-24
also i installed banshee. it opens but nothing shows up. (screenshot)
and after i force quit it its still running. it takes up like 45% of my CPU!

---

### Post by MooPi on 2009-12-24
Try to start Banshee from terminal, as it will show you any error messages when things go wrong. Also to stop the program open a second terminal and type  ```
xkill
``` This will give you an X or skull and cross bones to kill banshee.

---

### Post by phillychease on 2009-12-25
cool. i get this after i run it. how do i get the plug ins?

```
phillychease@phillychease:~$ banshee
[Info  11:00:36.313] Running Banshee 1.5.2: [Ubuntu 9.10 (linux-gnu, i486) @ 2009-12-17 05:12:39 UTC]

(/usr/lib/banshee-1/Banshee.exe:2031): GLib-WARNING **: g_set_prgname() called multiple times
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
[Warn  11:00:40.251] Caught an exception - SIGILL (in `Banshee.GStreamer')
  at (wrapper managed-to-native) Banshee.GStreamer.Service:gstreamer_initialize (bool,Banshee.GStreamer.Service/BansheeLogHandler)
  at Banshee.GStreamer.Service.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  11:00:40.251] Extension `Banshee.GStreamer.Service' not started: SIGILL

```

---

### Post by phillychease on 2009-12-25
nvm i got it

---

