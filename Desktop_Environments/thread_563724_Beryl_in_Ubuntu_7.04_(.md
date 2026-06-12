---
title: "Beryl in Ubuntu 7.04 :("
date: 2007-09-30
forum: Desktop Environments
---

### Post by neverdie on 2007-09-30
i have installed xserver-xgl and beryl. i run beryl and i get this: 

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension.

my xorg.conf says:

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
EndSection

i dont know what's wrong... :/

---

### Post by mikeserv on 2007-09-30
First of all, why do you have two "Device" sections?  Secondly, try this at the command-line and output the results:

fglrxinfo

-Mike

---

### Post by neverdie on 2007-10-01
with fglrxinfo get this:

 Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 1.2 (2.0.6747 (8.40.4))

also, i reinstall ati drivers, and now my xorg.conf is like:

Section "Device"
        Identifier  "ati radeon x1400"
        Driver      "ati"
        Option      "UseFBDev" "true"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

is it better to have ati or fglrx drivers?
also I get this error/warning while trying to run various programs,

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

how can i fix it?

---

