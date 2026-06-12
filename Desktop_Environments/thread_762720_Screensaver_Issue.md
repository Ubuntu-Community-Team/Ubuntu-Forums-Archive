---
title: "Screensaver Issue"
date: 2008-04-22
forum: Desktop Environments
---

### Post by nonaguy on 2008-04-22
I have a dual-monitor workstation running Ubuntu 7.10, and I am having dificulty configuring the screen saver to my liking. I want when the screensaver launches to simply draw the desktop background image, fullscreen across both monitors, i.e. exactly how it displays on the desktop. (This is similar to the behavior of Windows XP if the screensaver is disabled and the system is locked). My current configuration is using chbg as an xscreensaver hack, I have a chbg scenario file, that when launched from the command line (with the "Screensaver: true" option set) displays as I desire it to, with the 2560x1024 image filling both 1280x1024 monitors, just like how it displays the desktop background. However when I launch chbg as an xscreensaver hack (I have tried both "Screensaver: true" & "Xscreensaver: true") with the same scenario file it displays the image squished onto the left monitor, i.e. the entire 2560x1024 image is displaying at 1280x1024 on one monitor, the other goes black. Prior to this I experimented with glslideshow, which shrunk the image and displayed it on both monitors (at 1280x512, centered), and gnome-screensaver (never could get this to work better than Xscreensaver, which I prefer). So, please let me know what further information you need and I will be happy to post it, I have been struggling with this ever since I got my new system, so any help is greatly appreciated.

---

### Post by robaldred on 2008-04-23
I think there is some bugs/incompatibility with the screen saver and 3d effects on certain setups. I'm not certain, but I have issues too, the screen saver looks corrupt for me. When i turn off 3d effect the screensaver works fine.

---

