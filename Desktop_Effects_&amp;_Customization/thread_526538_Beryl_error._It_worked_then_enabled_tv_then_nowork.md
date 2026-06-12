---
title: "Beryl error. It worked then enabled tv then nowork."
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by brittney on 2007-08-15
Hi!
Ive searched the forum but i cant figure out what it is. 

1. I'm running Ubuntu feisty with a gforce fx7###.
2. It was working beautifully, installed with the enable desktop effects button. 
3. I connected the tv and in nvidia settings got the tv to work with cloning.
4. As soon the tv started to work beryl/compiz died.
5. I cant find where to change back the settings as it was.
6. I cant find log where compiz is loggin to, so i dont have an error msg either.
7. I dont have physical access to the box, its my mothers at my mothers!
8. I removed .compizconfig and .nvidia-settings-rc thinkin i would reset the settings i made but didnt work.

Please help I bet it is just some small setting somewhere that buggs it.

-bri

---

### Post by brittney on 2007-08-15
did everything in this thread and still didnt work.
[http://ubuntuforums.org/showthread.php?t=525842](http://ubuntuforums.org/showthread.php?t=525842)

-bri

---

### Post by dougfractal on 2007-08-15
If you save from nvidia-settings
you need to re-enable aiglx
> 
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by brittney on 2007-08-16
yeah tried that. Its allready added. Still no work. Where is the logfiles for compiz??

---

### Post by brittney on 2007-08-16
there is no errors in Xorg.0.log.

It says glx is initialised 

from Xorg.0.log
> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7800 GTX at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.70.02.11.10
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7800 GTX at PCI:1:0:0:
(--) NVIDIA(0):     Philips 190B (CRT-0)
(--) NVIDIA(0): Philips 190B (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.



what about 
> (--) Depth 24 pixmap format is 32 bpp
correct?

---

### Post by dougfractal on 2007-08-16
> (--) Depth 24 pixmap format is 32 bpp this is normal.

please post xorg.conf

---

### Post by brittney on 2007-08-16
my xorg.conf

[http://poobag.nordic-pua.net/rimpex/xorg.conf](http://poobag.nordic-pua.net/rimpex/xorg.conf)

---

### Post by dougfractal on 2007-08-16
> Option         "metamodes" "CRT: 1280x1024 +0+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"

to
>    Option         "TwinView" "1"  
    Option         "metamodes" "CRT: 1280x1024 +0+0, TV: 800x600 +1280+0; CRT: 1024x768 +0+0; CRT: 832x624 +0+0; CRT: 800x600 +0+0; CRT: 640x480 +0+0"

I think you will only get twinview in 1280x1024 res.

---

### Post by brittney on 2007-08-16
> **dougfractal said:**
> to


I think you will only get twinview in 1280x1024 res.

And this will fix the problem with compiz? isnt that just to make twinview workin which broke compiz from the beginning?

---

### Post by dougfractal on 2007-08-16
> Option         "AddARGBGLXVisuals" "True"

Section "Extensions"
    Option         "Composite" "Enable"
EndSection are already in xorg

The difference seems to be "TV: 800x600 +1280+0"  for tv composite/s-video out.  Your old xorg only had single view (no ,) twinview.

no promises. good luck.

---

