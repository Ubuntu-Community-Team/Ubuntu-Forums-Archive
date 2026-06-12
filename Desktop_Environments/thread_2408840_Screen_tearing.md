---
title: "Screen tearing"
date: 2018-12-24
forum: Desktop Environments
---

### Post by kumaran7 on 2018-12-24
I am experiencing screen tearing problem on lubuntu 18.10. im running on Amd HD 5450 video card.

---

### Post by Autodave on 2018-12-25
Did you just install this or did you upgrade from a previous version?

---

### Post by agklimit on 2019-01-27
I had the same issue, as follows.

This is freshly installed Ubuntu Studio (Ubuntu Xfce 18.10 Cosmic Cuttlefish)

This is the hardware:
ThinkPad Yoga 260

Intel Core i5-6200U Skylake

Graphics:
  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: Lenovo driver: i915 
  v: kernel bus ID: 00:02.0 chip ID: 8086:1916 
  Display: server: X.Org 1.20.1 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2) 
  v: 4.5 Mesa 18.2.2 compat-v: 3.0 direct render: Yes 

The one thing I tried was adding

Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod" "sna"
   Option      "TearFree" "true"
EndSection

In the file /etc/X11/xorg.conf

This did require a restart to work (possibly could've just restarted the service, but no matter.) Now when scrolling through text quickly and/or when watching high resolution video, I don't see any screen "tears" any more, so this must've worked!

---

### Post by Autodave on 2019-01-28
Glad that you got it straightened out!  Please remember to mark this thread as *solved* by going to the top of you original post and then going to *thread tools* and clicking on *Mark as solved.*

---

