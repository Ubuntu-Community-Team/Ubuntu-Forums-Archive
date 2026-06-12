---
title: "3D  Nvidia FX 5600 Ultra"
date: 2006-12-01
forum: Gaming &amp; Leisure
---

### Post by dontgetshocked on 2006-12-01
I have a Nvidia FX 5600 Ultra which has 3D support on the card, but my games with 3d wont play, they just lock up. How or what can i do to fix this? Is it a matter of just upgrading the driver or what?

Thanks,

---

### Post by Perfect Storm on 2006-12-01
Have you install the 3D binary driver?

Dapper - [http://doc.gwos.org/index.php/3D_Graphic_Cards_Dapper](http://doc.gwos.org/index.php/3D_Graphic_Cards_Dapper)
Edgy - [http://doc.gwos.org/index.php/3D_Graphic_Cards_Edgy](http://doc.gwos.org/index.php/3D_Graphic_Cards_Edgy)

---

### Post by holylucifer on 2006-12-01
Please note i had played unreal 2004 with no lockups with my nvidia fx5600 256mb,with installed drivers(legacy) + activated.

---

### Post by dontgetshocked on 2006-12-02
NOt working with 3d games. I have installed the nvidia-glx-legacy  driver via the synaptic manager. What else can I try? Belwo is the error message I get when I try to play a 3d game.

The Scorched3d process terminated due to configuration errors.
Display : ERROR: Failed to set video mode.
Error Message: Couldn't find matching GLX visual
----------------------------
Requested Display Mode:-
Driver=x11
Resolution=640x480x0 (windowed)
DepthBuffer=24
DoubleBuffer=On
ColorComponentSize=0

Scorched 3D Display : ERROR: Failed to set the display mode.
Ensure that no other application is exclusively using the graphics hardware.
Ensure that the current desktop mode has at least 24 bits colour depth.

---

### Post by po0f on 2006-12-02
dontgetshocked,

I have an FX5500 and *don't* use the legacy drivers.  Maybe try installing nvidia-glx instead?

---

### Post by slimdog360 on 2006-12-02
yep, use the nvidia-glx driver from synaptic and remember to use the command ```
sudo nvidia-glx-config enable
``` afterwards.

---

### Post by dontgetshocked on 2006-12-03
This is the error message I get when I try the enable command.


Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

---

### Post by Perfect Storm on 2006-12-03
```
sudo nano /etc/X11/xorg.conf
```

scroll down to **Section "Device"** and change "nv" to "nvidia", save and exit. Restart X.

---

### Post by dontgetshocked on 2006-12-03
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
____________________________________________________________________
Should this do it? Because it does not appear to make a difference!

---

### Post by po0f on 2006-12-03
dontgetshocked,

Did you restart X?  A Ctrl-Alt-Backspace should do it.  If you have any doubts, just restart your computer.

---

