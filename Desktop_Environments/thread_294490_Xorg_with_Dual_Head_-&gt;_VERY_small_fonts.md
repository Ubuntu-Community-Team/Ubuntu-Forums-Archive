---
title: "Xorg with Dual Head -&gt; VERY small fonts"
date: 2006-11-06
forum: Desktop Environments
---

### Post by info99 on 2006-11-06
Hi all!

I've some problems running Xorg in Dual Head mode, using the fglrx drivers from ATI (from the xorg-driver-fglrx package). When X11 is configured in Dual Head mode then the fonts of most of the programms are VERY SMALL. But for some programms (for example firefox) they are normal. This occured in KDE, Gnome as well as X11. Also some fonts in gdm are so small (for exmple the field where you enter the username) while others (for example the buttons to shut down or restart) have normal size fonts. These small fonts are so small that I cannot longer read them.

When using a single head setup all is fine.

Here is the important section from xorg.conf for the dual head setup:

```

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option     "DesktopSetup" "vertical,reverse"
        #Option      "DesktopSetup" "single"
        Option      "PowerState" "1"
        BusID       "PCI:1:0:0"
EndSection

```

The line for my single head setup is commented out.

One monitor is a 1680 x 1050 pixel TFT display inside the notebook while the second monitor is a external 1280 x 1024 pixel TFT.

I have the feeling that the fonts are getting smaller and smaller when I log in several times into X11.

Can someone give any hints? Also if not a solution some hints where do search might be very useful.

Thanks in advance
info99

---

### Post by info99 on 2006-11-07
No hints?

---

