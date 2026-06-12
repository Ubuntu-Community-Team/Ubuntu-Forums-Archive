---
title: "Quadro K420 on Ubuntu 16.04?"
date: 2017-05-17
forum: Desktop Environments
---

### Post by voyaflex00 on 2017-05-17
Hey All,

I have a fresh 16.04 install on a machine with Dual NVIDIA graphics cards, both Quadro K420. By default it is using the Xorg drivers but the mouse will flicker and one of the two screens I have is very blurry. Each monitor is plugged into it's own graphics card via displayport or DVI. 

I ventured to install the NVIDIA supported graphics drivers(340, 358, 370, 381). All the graphics drivers I attempted to install would install successfully. Except, upon reboot the secondary display would not have anything display, as if the cable was not plugged in.

I went into the nvidia-settings control panel, and sure enough, the second display is disabled. So I enabled it and it becomes X screen 1 and I applied the settings and saved the configuration into /etc/X11/xorg.conf. Then restarted.

The machine now detects the second screen and it will be lit, but black. I can move the mouse over and it has the "X" as the cursor as if there is no X server started on that side. Also, the regular Display settings in Ubuntu will not detect two seperate screens with NVIDIA graphics, only one. 

So basically with NVIDIA graphics installed I cannot get both screens functioning. 

Any help is greatly appreciated.

---

