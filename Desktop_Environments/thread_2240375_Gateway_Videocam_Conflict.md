---
title: "Gateway Videocam Conflict"
date: 2014-08-19
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-08-19
Folks,

A friend has Ubuntu 14.04 installed on her Gateway laptop after problems with Windows 7

I can access the computer via ssh including her desktop via ssh tunnel and VNC so am able to carry out tweaks etc.

Problem; she has an integrated webcam which does NOT work - tried cheese, skype and gimp, gstreamer-properties says 'no device on the video tab.

Not sure if it ever worked under Windows BUT dmesg shows a video conflict, lsusb or lspci show no video device.

lsmod shows;
```
video                  18903  1 acer_wmi
```

And the video entries (including the conflict) in dmesg shows;
```
[    0.527635] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cefff])
[    0.757911] pci 0000:00:01.0: Boot video device
[   14.769154] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.807035] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   14.828003] acer_wmi: Brightness must be controlled by acpi video driver


```

There is also no /dev/video

Any suggestions would be appreciated.

Geffers

---

