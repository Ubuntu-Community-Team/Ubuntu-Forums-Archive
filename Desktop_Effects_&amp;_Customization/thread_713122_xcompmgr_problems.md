---
title: "xcompmgr problems"
date: 2008-03-02
forum: Desktop Effects &amp; Customization
---

### Post by supersonicdarky on 2008-03-02
When I run xcompmgr I just get a series of errors:

```

kernel@laptop:~$ xcompmgr 
error 8 request 155 minor 4 serial 620
error 180 request 155 minor 8 serial 621
error 180 request 155 minor 8 serial 671
error 180 request 155 minor 8 serial 702
error 180 request 155 minor 8 serial 733
error 180 request 155 minor 8 serial 764
error 180 request 155 minor 8 serial 795
error 180 request 155 minor 8 serial 826
error 180 request 155 minor 8 serial 857
error 180 request 155 minor 8 serial 888
error 180 request 155 minor 8 serial 919
error 180 request 155 minor 8 serial 950
error 180 request 155 minor 8 serial 981
error 180 request 155 minor 8 serial 1012
error 180 request 155 minor 8 serial 1043
error 180 request 155 minor 8 serial 1074
error 180 request 155 minor 8 serial 1105
error 180 request 155 minor 8 serial 1136
error 180 request 155 minor 8 serial 1167
error 180 request 155 minor 8 serial 1198
error 180 request 155 minor 8 serial 1229
error 180 request 155 minor 8 serial 1260
error 180 request 155 minor 8 serial 1291
error 180 request 155 minor 8 serial 1322
error 180 request 155 minor 8 serial 1353
error 180 request 155 minor 8 serial 1384
error 180 request 155 minor 8 serial 1415
error 180 request 155 minor 8 serial 1446
error 180 request 155 minor 8 serial 1477
error 180 request 155 minor 8 serial 1508
error 180 request 155 minor 8 serial 1539
error 180 request 155 minor 8 serial 1570
error 180 request 155 minor 8 serial 1601
error 180 request 155 minor 8 serial 1632
error 180 request 155 minor 8 serial 1663
error 180 request 155 minor 8 serial 1694
error 180 request 155 minor 8 serial 1725
error 180 request 155 minor 8 serial 1756
error 180 request 155 minor 8 serial 1787
error 180 request 155 minor 8 serial 1818
error 180 request 155 minor 8 serial 1849
error 180 request 155 minor 8 serial 1880
error 180 request 155 minor 8 serial 1911
error 180 request 155 minor 8 serial 1942
error 180 request 155 minor 8 serial 1973
error 180 request 155 minor 8 serial 2004
error 180 request 155 minor 8 serial 2035
error 180 request 155 minor 8 serial 2066
error 180 request 155 minor 8 serial 2097
error 180 request 155 minor 8 serial 2128
error 180 request 155 minor 8 serial 2159
error 180 request 155 minor 8 serial 2190
error 180 request 155 minor 8 serial 2221
error 180 request 155 minor 8 serial 2252
error 180 request 155 minor 8 serial 2283
error 180 request 155 minor 8 serial 2314
error 180 request 155 minor 8 serial 2345
error 180 request 155 minor 8 serial 2376
error 180 request 155 minor 8 serial 2407
error 180 request 155 minor 8 serial 2438
error 180 request 155 minor 8 serial 2469
error 180 request 155 minor 8 serial 2500
error 180 request 155 minor 8 serial 2531
error 180 request 155 minor 8 serial 2562
error 180 request 155 minor 8 serial 2593
error 180 request 155 minor 8 serial 2624
error 180 request 155 minor 8 serial 2655
error 180 request 155 minor 8 serial 2686
error 180 request 155 minor 8 serial 2717
error 180 request 155 minor 8 serial 2748
error 180 request 155 minor 8 serial 2779
error 180 request 155 minor 8 serial 2810
error 180 request 155 minor 8 serial 2841
error 180 request 155 minor 8 serial 2872
error 180 request 155 minor 8 serial 2903
error 180 request 155 minor 8 serial 2934
error 180 request 155 minor 8 serial 2965
error 180 request 155 minor 8 serial 2996
error 180 request 155 minor 8 serial 3027
error 180 request 155 minor 8 serial 3058
error 180 request 155 minor 8 serial 3089
error 180 request 155 minor 8 serial 3120
error 180 request 155 minor 8 serial 3151
error 180 request 155 minor 8 serial 3182
error 180 request 155 minor 8 serial 3213
error 180 request 155 minor 8 serial 3244
error 180 request 155 minor 8 serial 3275
error 180 request 155 minor 8 serial 3306
error 180 request 155 minor 8 serial 3337
error 180 request 155 minor 8 serial 3368
error 180 request 155 minor 8 serial 3399
error 180 request 155 minor 8 serial 3430
error 180 request 155 minor 8 serial 3461
error 180 request 155 minor 8 serial 3492
error 180 request 155 minor 8 serial 3523
error 180 request 155 minor 8 serial 3554
error 180 request 155 minor 8 serial 3585
error 180 request 155 minor 8 serial 3616
error 180 request 155 minor 8 serial 3647
error 180 request 155 minor 8 serial 3678
error 180 request 155 minor 8 serial 3709
error 180 request 155 minor 8 serial 3740
error 180 request 155 minor 8 serial 3771
error 180 request 155 minor 8 serial 3802
error 180 request 155 minor 8 serial 3833
error 180 request 155 minor 8 serial 3864
error 180 request 155 minor 8 serial 3895
error 180 request 155 minor 8 serial 3926

```

I tried adding composite and render to xorg.conf but no luck

```

kernel@laptop:~$ cat /etc/X11/xorg.conf 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
        Option          "RENDER"        "True"
EndSection

```

I had it working before I formatted with no problems. I have sis m760gx which doesn't have 3d acceleration support so everything is running of the cpu.

---

