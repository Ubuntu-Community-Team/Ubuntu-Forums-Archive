---
title: "Pivot function / XRandR? / ATI drivers? / VNC?"
date: 2005-05-17
forum: Desktop Environments
---

### Post by zer on 2005-05-17
Hi there,

I am trying to enable the Pivot function for my TFT monitor.
My video card is an ATI Radeon 9800 Pro.
Ok, what i have tried until now:
[list]
[*]Use the command xrandr:
[/list]
```
xrandr
```gives
```
SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 339mm x 271mm )  *60
 1   1152 x 864    ( 339mm x 271mm )   60
 2   1024 x 768    ( 339mm x 271mm )   60
 3    832 x 624    ( 339mm x 271mm )   60
 4    800 x 600    ( 339mm x 271mm )   60
 5    720 x 400    ( 339mm x 271mm )   60
 6    640 x 480    ( 339mm x 271mm )   60
 7    640 x 350    ( 339mm x 271mm )   60
 8    640 x 400    ( 339mm x 271mm )   60
 9   1280 x 960    ( 339mm x 271mm )   60
 10  1280 x 768    ( 339mm x 271mm )   60
 11  1280 x 800    ( 339mm x 271mm )   60
 12  1152 x 768    ( 339mm x 271mm )   60
Current rotation - normal
Current reflection - none
**Rotations possible - normal**
Reflections possible - none
```

[list]
[*]Using another video driver (good idea?)
[/list]
```
/etc/X11/xorg.conf
```
```
Driver          "fbdev"
```
Now, X won't start because it says that there is no module named "fbdev". Hm..any other distribution i tried, worked with fbdev :-/. Do i have to recompile the kernel?

[list]
[*]VNC (first results)
[/list]
Ok, i downloaded [this cool hack](www.freesoft.org/software/vncrotation), and with vncserver and xvncviewer i can use the xrandr command.
Now, the problem is that my mouse is still in normal position (very bad :-/).
So i tried to integrate the VNC thing into X.
I added a line in /etc/X11/xorg.conf:
```
Load        "vnc"
```
If this line would be accepted ("the module doesn't exist" (where can i get it? ;)), i think i could get it working.

Is there anybody out here, who had it managed to get the the Pivot (Rotate) Function working?

I will be appreciated for every tip! :-)

PS: Sorry for my bad english..

---

### Post by zer on 2005-06-07
Ok, i solved the fbdev problem and have now a rotated Display.
You have to use 16Bit maximum with the fbdev driver and thats it.

But ATI, I'm waiting for support for rotation!

---

