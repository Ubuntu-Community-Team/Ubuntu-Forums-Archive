---
title: "Display resolution problems"
date: 2018-05-15
forum: Desktop Environments
---

### Post by alexvielma on 2018-05-15
Hi! i've just instaled xubuntu 16.04 and it works perfect but there is a problem with the display resolution. It only show me default option and the only screen resolution available is 640x480 73Hz but before installing xubuntu i tried it and the screen resolution was the original for my screen 1280x1024 60Hz.

Note: I'm actually using xubuntu 18.04 and there is still the problem.

---

### Post by alexvielma on 2018-05-15
xrandr command says:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480       73.00*

---

### Post by alexvielma on 2018-05-15
And the command inxi -G says:

Graphics:  Card: VIA CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev (unloaded: modesetting,vesa)
           Resolution: 640x480@73.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 128 bits)
           version: 3.3 Mesa 18.0.0-rc5

---

### Post by Autodave on 2018-05-15
Have you tried going into Settings -> Additional Drivers  to see if it finds anything?

---

### Post by alexvielma on 2018-05-15
Yes, i did. but says there are not additional drivers available

---

### Post by dino99 on 2018-05-15
Are you using xserver-xorg-video-openchrome driver ?

---

### Post by alexvielma on 2018-05-15
im not sure.. How to see it?

---

### Post by alexvielma on 2018-05-15
I solved it!! thanks dino99.

The driver wasn't installed so i did this in terminal:
[INDENT]   sudo add-apt-repository ppa:xorg-edgers/ppa

      sudo apt-get install xserver-xorg-video-openchrome

Then Reboot and it detects my Screen! 

 [/INDENT]

---

