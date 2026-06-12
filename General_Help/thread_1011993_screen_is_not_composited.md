---
title: "screen is not composited"
date: 2008-12-15
forum: General Help
---

### Post by xinloiemnham2 on 2008-12-15
I have this notification when loging in ubuntu :

[IMG]http://http://img208.imageshack.us/img208/7076/screenshotscreenisnotcotg0.png[/IMG]

I searched with key word **screen is not composited** and there is a result that closest to me. It said **Metacity and Compiz fight to be "compositing manager"** and **If the GConf key /apps/metacity/general/compositing_manager is set to true, Compiz cannot start**. But my gconf key is not set true.
Here is output of compiz command :
```
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```
My VGA is onboard : Intel GMA 950

---

### Post by Wartender on 2008-12-15
maybe if you press alt+f2 and type compiz --replace?
i'm not sure at all though.. i've only seen this done for metacity, you should probably wait to see if someone gives the ok.

---

