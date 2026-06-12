---
title: "ATI X1300, Eternal Lands freeze"
date: 2009-05-01
forum: General Help
---

### Post by Gorlist on 2009-05-01
Good day, since a fresh install to 9.04 ive been having problems with Eternal Lands. Running a ATI X1300 using opensource drivers.

Eternal Lands will load, display fine then lock after 3 seconds (mouse cursor will still be active but the desktop has frozen). Requires a manual reboot to recover.

Before it locks I get 0 - 1 FPS :) 

Ive now modified my Xorg slightly too the following:

```
Section "Device"
Identifier "Configured Video Device"
Driver "radeon"
Option "DRI"
Option "AGPFastWrite" "on"
Option "AccelMethod" "EXA"
Option "AccelDFS" "true"
Option "DynamicClocks" "false"
EndSection
```

Much better performance, 26 to 30 FPS however same problem with the crash.

Any suggestions?

Tried modifying all the ingame options, vary the graphical settings. Compiz is disabled.  

Best Regards,
            James

---

### Post by Gorlist on 2009-05-03
no suggestions at all?

---

### Post by Gorlist on 2009-05-06
suspect its related to this:

[http://www.eternal-lands.com/forum/index.php?showtopic=49536](http://www.eternal-lands.com/forum/index.php?showtopic=49536)

---

