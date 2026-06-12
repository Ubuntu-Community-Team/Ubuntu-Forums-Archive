---
title: "Any xorg.conf options to interactively select the layout to run?"
date: 2009-02-26
forum: Desktop Environments
---

### Post by skotos on 2009-02-26
I currently run two X configurations: the first one with a secondary display whose resolution is set to 1400x1050 and the second with a TV as a secondary display.

Since both of them work fine when a second display is not attached, no problem arises if I work in a stand alone environment, but it is annoying, every time I switch from my office to the TV if I forget to apply the change not informing X I have a different secondary display.

Is there any way to force X to show me a choice before coming up and, after a time out, choose a default configuration like we do with *grub*?

Both the configurations are available in the same xorg.conf. I simply rem out one profile to switch from one configuration to the other: see ***Section "ServerFlags"***, and the 2 *Section "ServerLayout"*.

[php]
Section "ServerLayout"
    Identifier     "LayoutOfLCDandElectron19BlueIII"
    Screen      0  "ScreenOf9815WKMI" 0 0
    Screen      1  "ScreenOfElectron19BlueIII" RightOf "ScreenOf9815WKMI"
EndSection

Section "ServerLayout"
    Identifier     "LayoutOfLCDandSonyTV"
    Screen      0  "ScreenOf9815WKMI" 0 600
    Screen      1  "ScreenOfSonyTV" Above "ScreenOf9815WKMI"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
#    Option         "DefaultServerLayout" "LayoutOfLCDandElectron19BlueIII"
    Option         "DefaultServerLayout" "LayoutOfLCDandSonyTV"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "MonitorOf9815WKMI"
    VendorName     "ACER"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 66.0
    VertRefresh     0.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "MonitorOfElectron19BlueIII"
    VendorName     "LACIE"
    ModelName      "LAC electr19b3"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "MonitorOfSonyTV"
    VendorName     "SONY"
    ModelName      "TV-0"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "NVIDIAportToLCDof9815WKMI"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "NVIDIAportToExternalDevice"
    Driver         "nvidia"
    Option         "NoLogo" "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "ScreenOf9815WKMI"
    Device         "NVIDIAportToLCDof9815WKMI"
    Monitor        "MonitorOf9815WKMI"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "ScreenOfElectron19BlueIII"
    Device         "NVIDIAportToExternalDevice"
    Monitor        "MonitorOfElectron19BlueIII"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1400x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "ScreenOfSonyTV"
    Device         "NVIDIAportToExternalDevice"
    Monitor        "MonitorOfSonyTV"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/php]If it were possible to solve this issue, I might, for instance, configure a secondary display for each customer I am visiting (1024x768, 800x600, on the left side, on the right, above, below, different refresh rates, ...)

Thanks in advance!

---

### Post by smani on 2009-02-26
You could try the following:
- You create two variants of xorg.conf, say xorg.conf.monitor1 and xorg.conf.monitor2.
- Write a script that, at startup, detects the monitor attached and renames the correct xorg.conf variant to xorg.conf (in /etc/X11 clearly). To detect you monitor, you could look ad the information the monitor provides in /proc/acpi/video/... where the following directories depend on graphicscard and attached monitors. A script would be
```

#!/bin/bash
monitor=`cat /proc/acpi/video/<...> | grep device_id`;
if [ "$monitor" == "device_id: <...>" ]; then
mv /etc/X11/xorg.conf.monitor1 /etc/X11/xorg.conf;
else
mv /etc/X11/xorg.conf.monitor2 /etc/X11/xorg.conf;
fi;
exit 0;

```
- Place the script (remember to set it as executable) in /etc/rc2.d with the correct naming format, i.e. S29setdisplay (S=start, 29=start order - important before the gdm!)

This is just an idea, I have not tested anything similar, so please be carefull:) And clearly make a backup copy of the xorg.conf somewhere;)

---

### Post by skotos on 2009-02-28
> **smani said:**
> You could try the following:
- You create two variants of xorg.conf, say xorg.conf.monitor1 and xorg.conf.monitor2.
- Write a script that, at startup, detects the monitor attached and renames the correct xorg.conf variant to xorg.conf (in /etc/X11 clearly). To detect you monitor, you could look ad the information the monitor provides in /proc/acpi/video/... where the following directories depend on graphicscard and attached monitors. A script would be
```

#!/bin/bash
monitor=`cat /proc/acpi/video/<...> | grep device_id`;
if [ "$monitor" == "device_id: <...>" ]; then
mv /etc/X11/xorg.conf.monitor1 /etc/X11/xorg.conf;
else
mv /etc/X11/xorg.conf.monitor2 /etc/X11/xorg.conf;
fi;
exit 0;

```- Place the script (remember to set it as executable) in /etc/rc2.d with the correct naming format, i.e. S29setdisplay (S=start, 29=start order - important before the gdm!)

This is just an idea, I have not tested anything similar, so please be carefull:) And clearly make a backup copy of the xorg.conf somewhere;)
Thank you very much, smani. I am going to try it this afternoon.

---

