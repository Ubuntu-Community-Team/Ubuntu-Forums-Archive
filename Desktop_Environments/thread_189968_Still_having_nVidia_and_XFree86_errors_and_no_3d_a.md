---
title: "Still having nVidia and XFree86 errors and no 3d accel"
date: 2006-06-05
forum: Desktop Environments
---

### Post by graabein on 2006-06-05
This is pretty wierd. I've followed the wiki and I've posted my problems at the end of [this thread]("http://ubuntuforums.org/showthread.php?t=182289"). I didn't know where to go so I did a keyword search and put it in there.

I still have no direct rendering. ](*,) 

[I]$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No[/I]

I've had this problem for a long time. All of Breezy's reign I think. But now I really want XGL/Compiz coolness so I'm close to wiping my system and starting fresh.

---

### Post by CallsignBaron on 2006-06-05
Did you edit your xorg.conf file to use the nvidia driver?

---

### Post by graabein on 2006-06-06
Yes, I followed the wiki and ran "sudo nvidia-xconfig" before I rebooted. I checked xorg.conf and it has Driver=nvidia and RenderAccel=true.

---

### Post by graabein on 2006-06-11
*bump*

---

### Post by tseliot on 2006-06-11
[QUOTE=graabein]This is pretty wierd. I've followed the wiki and I've posted my problems at the end of [this thread]("http://ubuntuforums.org/showthread.php?t=182289"). I didn't know where to go so I did a keyword search and put it in there.

I still have no direct rendering. ](*,) 

[I]$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No[/I]

I've had this problem for a long time. All of Breezy's reign I think. But now I really want XGL/Compiz coolness so I'm close to wiping my system and starting fresh.[/QUOTE]
Try starting a new thread here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&page=2&order=desc")

---

