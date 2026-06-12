---
title: "Dual Monitor support problem Dell D630"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeanM on 2009-03-18
Hello all.

I've been using Ubuntu for about 6 months now.  It's the best.  I have one small problem.  I have searched lots for answers to this particular problem, but have yet to find a solution.

I am using Intrepid on a D630.  I have a Dell 1905FP monitor - native resolution is 1280x1024.  The problem is with the dual monitor setup, I always end up with 1024x768 on the 1905FP.  Here's what's in my xorg.conf:
--------------------------------------------------------------------
Section "Monitor"
        Identifier      "Laptop Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
EndSection

Section "Monitor"
        Identifier      "Dell Monitor"
        VendorName      "Dell"
        ModelName       "1905FP"
        HorizSync       31.5-48.5
        VertRefresh     40-70
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Laptop Screen"
        Device          "0 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Laptop Monitor"
        SubSection "Display"
                Depth 24
                Modes "1280x800"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Dell Screen"
        Device          "1 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Dell Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Laptop Screen" 0 0
        Screen 1        "Dell Screen" RightOf "Laptop Screen"
        Option "DualHead" "true"
EndSection

Section "Device"
        Identifier      "0 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver "intel"
EndSection

Section "Device"
        Identifier      "1 Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver "intel"
EndSection
-----------------------------------------------------------------
Any ideas?

---

