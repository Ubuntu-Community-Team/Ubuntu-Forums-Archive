---
title: "Cannot decrease screen resolution"
date: 2010-01-02
forum: Desktop Environments
---

### Post by TheOtherShoe on 2010-01-02
I have been struggling with this for a long time.  I am running with an nvidia 7600GT with the latest proprietary binary driver in Karmic on a laptop with a native screen resolution of 1680x1050.  Everything runs fine at the native resolution.  But I want to be able to decrease the resolution for better performance/compatibility in games.

Ever since Xorg stopped using a configuration file I have not been able to find any way to change the screen resolution.  nvidia-settings lists the native resolution of my screen, but does not provide any other options.  The Gnome display tool says that my graphics driver does not have the necessary extensions that it needs.  I tried creating an xorg.conf file with some different display modes, but that did not seem to work either.

Does anybody know if there is a way I can change the screen resolution?  I would like to be able to play Morrowind :)

---

### Post by TheOtherShoe on 2010-01-02
I took another shot at creating an xorg.conf file using nvidia-settings to generate the initial file.  I added two non-native metamodes with no success.  Here is some of the Xorg log output:

```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1680x1050 +0+0, 1280x800 +0+0, 1024x768 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7600 (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.64.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7600 at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "1280x800+0+0"
(WW) NVIDIA(0): Invalid display device in Mode Description "1024x768+0+0"
(WW) NVIDIA(0): Not using mode description "1280x800+0+0"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): Not using mode description "1024x768+0+0"; unable to map to
(WW) NVIDIA(0):     display device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050+0+0,1280x800+0+0,1024x768+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (129, 126); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
```

I can see that the new metamodes are interpreted correctly by Xorg.  But they are then rejected for some reason.

---

### Post by TheOtherShoe on 2010-01-02
It turns out that this problem is specific to my screen, which is a Seiko DFP on a Compal HEL80 laptop.  I found some other threads with helpful information:

[http://ubuntuforums.org/archive/index.php/t-636618.html](http://ubuntuforums.org/archive/index.php/t-636618.html)
[http://www.nvnews.net/vbulletin/showthread.php?p=1479295#post1479295](http://www.nvnews.net/vbulletin/showthread.php?p=1479295#post1479295)
[http://ubuntuforums.org/showthread.php?t=423438](http://ubuntuforums.org/showthread.php?t=423438)
[http://ubuntuforums.org/showthread.php?p=129379#post129379](http://ubuntuforums.org/showthread.php?p=129379#post129379)

I have not quite gotten the solution from those first two threads working yet.  It seems to require manually configuring modelines in Xorg with very specific parameters.

---

