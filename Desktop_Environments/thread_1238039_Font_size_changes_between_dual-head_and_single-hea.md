---
title: "Font size changes between dual-head and single-head"
date: 2009-08-12
forum: Desktop Environments
---

### Post by cmreigrut on 2009-08-12
I have a Dell Vostro 1720 laptop running Kubuntu 9.04, which has an NVIDIA GeForce 9600M GS and a 1920x1200 LCD.  I have an external LCD as well, which also supports 1920x1200.  I have it set up nicely using TwinView in order to support a dual-head environment at 3840x1200, and I have the following in my xorg.conf to allow me to use KRandRTray to switch between single-head and dual-head:

```

    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1920x1200 +0+0, DFP: 1920x1200 +1920+0; CRT: NULL, DFP: 1920x1200 +0+0"

```
Frankly, it rocks..._except_ that the font size actually changes when I switch between 1920x1200 single-head and 3840x1200 dual head, and it's driving me crazy.

Steps to recreate:
1) Bring up Kubuntu in dual-head mode.  Kate displays approximately 62.5 lines when maximized above the standard panel.
2) Use KRandRTray to move to single-head mode.  Kate still displays 62.5 lines.
3) Unplug external monitor, log out, and restart X server.  The login dialog is now much larger.
4) Log in and start Kate.  Now I only see approximately 44.75 lines when maximized above the standard panel.

Has anyone else seen this?  If I change my system font sizes from 8pt to 7pt then it's about the same, but it would be crazy to do that every time I switch between dual-head and single-head.  Why would 8pt fonts change their actual pixel size (especially when the HEIGHT of the screen isn't changing at all)?!

---

### Post by krazyd on 2009-08-12
..sounds like a DPI issue. What happens when you go to System Settings > Appearance > Fonts, and Force Fonts DPI to some value?

Alternatively, I'm sure there's a way to set DPI in xorg.conf - I'm not sure of the syntax, but you can google it. I did and found these pages for starters:
[http://linux-blog.org/kde-and-xorg-fonts-and-dpi/](http://linux-blog.org/kde-and-xorg-fonts-and-dpi/)
[http://wiki.archlinux.org/index.php/Xorg#Display_Size.2FDPI](http://wiki.archlinux.org/index.php/Xorg#Display_Size.2FDPI)

---

### Post by Zorael on 2009-08-12
I don't get sane DPI at the kdm greeter (login screen) unless I manually set it to 96. Since this is before user-specific settings are read, the only way I found to do it was to add a **-dpi 96** argument to the X command, though there's probably a xorg.conf option as well.

I'm not sure what approach would be the best for your situation. FWIW, in **/etc/kde4/kdm/kdmrc** (excerpt);
```
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/usr/bin/X
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
**ServerArgsLocal=-br -nolisten tcp [COLOR="RoyalBlue"]-dpi 96[/COLOR]**
```

---

### Post by cmreigrut on 2009-08-13
I would have never come up with the DPI issue...thank you both!

Thus far, simply setting "Force fonts DPI" in System Settings->Appearance->Fonts to 96DPI has done the trick.

I'm guessing that changing kdmrc would work, too, but I can live with the larger fonts at login.

---

