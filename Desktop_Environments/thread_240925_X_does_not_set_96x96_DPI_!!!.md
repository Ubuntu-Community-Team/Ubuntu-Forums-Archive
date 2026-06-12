---
title: "X does not set 96x96 DPI !!!"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Jabran Asghar on 2006-08-21
Hi,

How can I set 96x96 DPI in Dapper, Gnome?

I have dell 19" TFT, resolution 1280x1024.

I have set 96DPI in Font preferences, as well as "DisplaySize 378 270" in xorg.conf, but still "xdpyinfo | grep resolution" gives "85x86"!

How can I make it 96x96?

Jabran

---

### Post by xtknight on 2006-08-21
Shouldn't the DisplaySize be 376 301 roughly?

(Active Area for a 19" 1280x1024 TFT)
[http://www.samsung.com/Products/TFTLCD/Monitor/LTM190EX/LTM190EX.htm](http://www.samsung.com/Products/TFTLCD/Monitor/LTM190EX/LTM190EX.htm)

---

### Post by Jabran Asghar on 2006-08-22
When the value that I put didn't work, then I actually tried changing the values even randomly (followed by restart of X) to see if that change any bits, but that didn't work. To my observation, only changinv the DPI value in Fonts-Preferences shows some effect, but even if I give 96DPI (or whatever), xdpyinfo always gives 85x86. 

One more observation: If I stop GDM, and then set "defaultservargs" parameter to "-dpi 96" in "/usr/bin/startx", then start Gnome with "startx" --> xdpyinfo gives DPI 100x100.

This gives some clue that DPI is perhaps being set in some hierarchy at mulitple points, and each point has some priority. When we start Gnome through differnt method, the DPI value with highest priority in that path gets set. Not sure though, what are the points where the DPI can be specified and about what is their priority order.

I shall try the values you mentioned, and then post back if that corrected the problem.

Thanks.

---

### Post by Johan! on 2006-08-22
Do you have a nVidia graphics card?
It gets all settings directly from your monitor.
Read [this](http://download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-y.html) at the nVidia site.


You can try this setting in your xorg.conf
```
Option "UseEdidDpi" "FALSE"
```

> Option "DPI" "string"

    This option specifies the Dots Per Inch for the X screen; for example:

        Option "DPI" "75 x 85"

    will set the horizontal DPI to 75 and the vertical DPI to 85. By default, the X driver will compute the DPI of the X screen from the EDID of any connected display devices. See Appendix Y, Dots Per Inch for details. Default: string is NULL (disabled).
Option "UseEdidDpi" "string"

    By default, the NVIDIA X driver computes the DPI of an X screen based on the physical size of the display device, as reported in the EDID. If multiple display devices are used by the X screen, then the NVIDIA X screen will choose which display device to use. This option can be used to specify which display device to use. The string argument can be a display device name, such as:

        Option "UseEdidDpi" "DFP-0"

    or the argument can be "FALSE" to disable use of EDID-based DPI calculations:

        Option "UseEdidDpi" "FALSE"

    See Appendix Y, Dots Per Inch for details. Default: string is NULL (the driver computes the DPI from the EDID of a display device and selects the display device).


---

### Post by codejunkie on 2006-08-22
adding this to the monitor section and restarting the xserver should fix it
```
Option   "DPI"   "96 x 96"
```at least this works on my nvidia card.

---

### Post by Jabran Asghar on 2006-08-23
> **codejunkie said:**
> adding this to the monitor section and restarting the xserver should fix it
```
Option   "DPI"   "96 x 96"
```at least this works on my nvidia card.

It worked. Now xdpyinfo reports 96x96 DPI. (There seems no difference on the display of fonts though. Only changing Font->Preferences DPI had effect on fonts' display.)

Thanks everyone.

---

