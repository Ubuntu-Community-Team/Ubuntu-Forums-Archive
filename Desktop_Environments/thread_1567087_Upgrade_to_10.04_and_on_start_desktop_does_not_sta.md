---
title: "Upgrade to 10.04 and on start desktop does not startup"
date: 2010-09-03
forum: Desktop Environments
---

### Post by darrowj on 2010-09-03
I recently updated to Ubuntu 10.04.  On this same machine I've used Ubuntu for 3 or 4 years now.  Upgrading from 8 - 9 - 10.  I love Ubuntu and use it as my everyday work environment.

Anyway, recently when I start my machine in the morning it boots to commandline instead of the desktop.  For the last couple days I boot to safe-mode and do a package repair.  Sometimes more than once.  Eventually I get the desktop to start but it is annoying.  

When trying to boot to Fail Safe Graphics Mode(?) I get an error stating: "Fatal Server Error: No Screens."  The message referred me to /var/log/Xorg/failsafe.log.  Here is a snippet of the end of that log file:

[I]
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules/libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found  [/I] 

Also, I'm using an NVidia graphics card on an HP machine.  I installed the "current version" accelerated graphics driver which it says is proprietary.

---

### Post by quixote on 2010-09-05
I've had better luck with the open source nvidia driver than with Nvidia's own.  Seriously.  Next time you're reinstalling drivers anyway, you could try getting "xserver-xorg-video-nouveau" in synaptic, or running at the command line:```
sudo apt-get install xserver-xorg-video-nouveau
```(If you're in recovery mode, you won't need the "sudo" part.

Be nice if that was all it took!

---

