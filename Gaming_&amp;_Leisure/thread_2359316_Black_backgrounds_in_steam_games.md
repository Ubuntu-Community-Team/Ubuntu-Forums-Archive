---
title: "Black backgrounds in steam games"
date: 2017-04-22
forum: Gaming &amp; Leisure
---

### Post by tuese on 2017-04-22
Some steam games loading with black screens, backgrounds, images. Examples:
Black screen when games loading - [https://i.imgur.com/uGNs0wb.png](https://i.imgur.com/uGNs0wb.png)
Team Fortress 2 - [https://i.imgur.com/lLwbVKl.jpg](https://i.imgur.com/lLwbVKl.jpg), [https://i.imgur.com/FyAU1M6.jpg](https://i.imgur.com/FyAU1M6.jpg)
Codename CURE - [https://i.imgur.com/VgrRkqh.jpg](https://i.imgur.com/VgrRkqh.jpg)
No More Room in Hell - [https://i.imgur.com/KTrlIqq.jpg](https://i.imgur.com/KTrlIqq.jpg)
Unturned - [https://i.imgur.com/HNtzTIc.jpg](https://i.imgur.com/HNtzTIc.jpg)
And there is this with steam tray icon - [https://i.imgur.com/oBC1lt6.png](https://i.imgur.com/oBC1lt6.png)

Xubuntu 16.04.02 64-bit. Tried "verify integrity" and changing video setting, nothing helps. 
```
Kernel: 4.8.0-46-generic x86_64 (64 bit gcc: 5.4.0)
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 chip-ID: 8086:0a16
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 12.0.6 Direct Rendering: Yes

```
Tried - [https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/ubuntu/updates") but problem stays the same.

Can someone help?[URL="https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates"]



[/URL]

---

### Post by Perfect Storm on 2017-04-22
Try:
```
sudo apt-get install libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386
```

---

### Post by tuese on 2017-04-22
Thank you very much! All problems solved!

---

