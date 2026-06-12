---
title: "Help with &quot;Double buffered visual&quot; error"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by hulet on 2007-04-11
Hello,

I just installed Feisty Fawn 7.04 to see what all this hype about Beryl is, unfortunately I couldn't get off the ground because of this error:
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Root visual is not a double buffered GL visual
beryl: Root visual is not a double buffered GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

I have searched all over the net on how to enable this on my ATI all-in-wonder rage 128 video card (yeah, I know an old vc) but so far nothing that really worked. Here is the relevant part of my xorg.conf (direct rendering is enabled and actually works):
```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

```
```

Section "Device"
        Identifier      "ATI Technologies Inc Rage 128 RF/SG AGP"
        Driver          "r128"
        BusID           "PCI:1:0:0"
        Option "EnablePageFlip" "true"
EndSection

```
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection 

```

And, a piece of /var/log/Xorg.0.log:
```
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
...

```

Can anyone please help me out on how to get this double buffered visual set up? Thanks.

---

### Post by fkdev on 2007-05-20
I think this will do it:
[http://lists.freedesktop.org/archives/xorg/2007-January/020919.html](http://lists.freedesktop.org/archives/xorg/2007-January/020919.html)

---

### Post by kknull on 2007-06-02
Hi,
I have the same problem, I have read the site you linked, but I don't know where is and how to install the "r128_dri.c" driver. Any suggestion?

Thanks!
KKnull.

---

### Post by kknull on 2007-06-04
up :(

---

### Post by raviyer on 2007-07-23
Well the r128_dri.c seems to be renamed to ati_dri.c or atidri.c depending on what source package you look at. In any case I got the source package for xserver-xorg-video-ati found the relevant line which now looks like:

      for (db = 0; db <= 1; d++)

to read as
      for (db = 1; db >= 0; db--)

but this still does not fix the problem. Also I noticed that the code above is in a case statement for 16 bit color depth only and so I switched to 16 bits color and it still did not work.

---

