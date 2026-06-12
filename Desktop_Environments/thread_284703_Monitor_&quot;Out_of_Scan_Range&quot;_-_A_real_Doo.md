---
title: "Monitor &quot;Out of Scan Range&quot; - A real Doozie"
date: 2006-10-26
forum: Desktop Environments
---

### Post by rebelfallen on 2006-10-26
I am trying to set up dual monitors. I have a GeForce FX 5200 card which supports duals. My main monitor is a Dell and my secondary is a Sony.

Here is my Xorg.conf file

```
Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Sony SDM-HS53"
 ### Comment all HorizSync and VertSync values to use DDC:
        HorizSync 28 - 48
        VertRefresh 57 - 63
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "vesa"
        VendorName  "Videocard vendor"
        BoardName   "nVidia Corporation NV34 [GeForce FX 5200]"
        VideoRam    20000
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Videocard0"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1024x768" "800x600"
        EndSubSection
EndSection

```


This doesn't seem to work even though it really should. I set the HorizSync and VertRefresh to the default values and still nothing. Anyone have some suggestions?

---

### Post by CatKiller on 2006-10-26
Do you **have** a Monitor0? Or the nvidia drivers? You appear to have only defined one video card output for that matter, too.

As far as I know, the "Out of Scan Range" message is equivalent to the "No Signal" message.

---

