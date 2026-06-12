---
title: "fgrlx and sddm problems"
date: 2015-06-13
forum: Desktop Environments
---

### Post by imrazor on 2015-06-13
I'm trying to get Kubuntu 15.04 working satisfactorily on my laptop, and am running into numerous issues with graphics drivers. For whatever reason, the OpenGL performance of the open source driver is no better than software rendering. Plus running a game with the open source driver causes reboots and crashes of the X desktop. Due to these issues, I had to go with fglrx-updates. This works better with games, but I'm having issues with the desktop, primarily I think with sddm.

The first symptom is that sddm-greeter crashes right after login. The desktop loads, but I'm welcomed with a crash report for sddm-greeter. The next obvious symptom is a krunner and/or kdeinit5 crash during reboot. Thirdly, if the session locks, it is impossible to unlock it. If you enter the correct password on the lock screen, the screen goes blank for a moment, then goes right back to the lock screen. And finally, the laptop will not resume from sleep. The backlight stays on, and the computer will not respond to any keyboard/mouse interaction.

Any suggestions for dealing with these issues? I can disable the lock screen entirely, but that's not the most secure way to run a PC. It occurred to me to replace sddm with a different display manager, but I'm not sure if that's possible with KDE 5/Plasma. If so, how would I go about it? Another possibility would be to revert to Kubuntu 14.10, but I really like the new desktop environment. However, I'm not sure that even that would prevent the fglrx crashes I'm seeing.

My laptop is a Dell Precision M6600 with an AMD Firepro M6100 GPU.

---

### Post by imrazor on 2015-06-24
The fix in this case was to move to Ubuntu and remove all traces of sddm. Really unfortunate, since I was enjoying the new DE. I couldn't get KDE to coexist with another display manager, so I had to ditch both sddm and KDE. However, Ubuntu seems to be running without a hitch.

---

