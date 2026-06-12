---
title: "Issue with certain rendering color font in gnome terminal"
date: 2019-01-27
forum: Desktop Environments
---

### Post by wolnosc92 on 2019-01-27
I have a annoying problem with gnome terminal. Some font color are not rendering properly. I try to change font type, size, nothing work, I have ugly font. It's happen only in gnome terminal, on another app, like Firefox, Libreoffice, all is good.

On the screen capture, it's appear not so bad due the zoom, but on my screen it's almost unreadable. It's look like on the pure red (and pure blue) color the subpixeling does't work.

screen capture :
[IMG]http://www.image-share.com/upload/3920/224.png[/IMG]
[IMG]http://www.image-share.com/upload/3920/225.png[/IMG]

I use Ubuntu 18.10, last update with GTX 750 TI (proprietary driver), my screen resolution:
 HDMI-0 connected primary **3840x2160**+0+0 (normal left inverted right x axis y axis) 608mm x 345mm
   3840x2160     60.00*+  59.94    50.00    30.00    29.97    25.00    23.98 
gnome-tweak scale font factor : 1.40 (back to 1.0 doesn't resolve the issue)

---

### Post by wolnosc92 on 2019-02-16
I found the problem. My GTX 750 TI can output in 4K@60Hz only in 4:2:2 chroma subsambling (due HDMI1.4). In other word, my graphic card compress HDMI signal and affect lot of "pure color". Then I bought a new graphic card GTX1050 who deliver 4K@60hz (HDMI2.0) in 4:4:4 (uncompressed signal), all is displayed correctly !

---

