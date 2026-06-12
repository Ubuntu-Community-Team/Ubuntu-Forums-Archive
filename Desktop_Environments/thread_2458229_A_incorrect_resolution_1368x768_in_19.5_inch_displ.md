---
title: "A incorrect resolution 1368x768 in 19.5 inch display"
date: 2021-02-19
forum: Desktop Environments
---

### Post by ginousi on 2021-02-19
We have a built-in 19.5 inch display in Tiger Lake platform,
install Ubuntu 20.04.2 LTS, in display resolution select list, a 1368x768(16:9) item be showed, but display spec support resolution is 1366x768,

Install Windows 10, resolution can be showed 1366x768 correctly.

Is it an known issue in Ubuntu?
or has method can fix it?


Thanks

[IMG]https://imgur.com/oWsdFiK[/IMG]

---

### Post by CelticWarrior on 2021-02-19
Not an issue.

---

### Post by ActionParsnip on 2021-02-19
What is the output of:
```

sudo lshw -C display; lsb_release -a; uname -a; xrandr

```

---

### Post by ActionParsnip on 2021-02-19
Wait are you quibbling 2 pixels here?

---

### Post by CelticWarrior on 2021-02-19
> **ActionParsnip said:**
> Wait are you quibbling 2 pixels here?
That seems to be the case indeed.

---

### Post by ActionParsnip on 2021-02-19
> **CelticWarrior said:**
> That seems to be the case indeed.
Yep, not an issue at all.It's half a millimetre in width. Why post a question for this...at all?

---

### Post by ginousi on 2021-02-20
> **ActionParsnip said:**
> What is the output of:
```

sudo lshw -C display; lsb_release -a; uname -a; xrandr

```

  ```
*-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 mode=1920x1080 visual=truecolor xres=1920 yres=1080
       resources: iomemory:600-5ff iomemory:400-3ff irq:157 memory:6002000000-6002ffffff memory:4000000000-400fffffff ioport:3000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff
```
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
Linux jed-6201103 5.8.0-44-generic #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
```
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 16384 x 16384
eDP-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 408mm x 230mm
   1920x1080     60.05 +  60.01    59.97    59.96    59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82* 
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by Yellow Pasque on 2021-02-21
> **ActionParsnip said:**
> Wait are you quibbling 2 pixels here?

You generally want the resolution to match the native resolution of the screen, so questioning 2 pixels isn't necessarily a bad idea.
However, in this case, 1366x768 isn't the native resolution of the screen, and 1360/1366/1368 x 768 isn't exactly 16:9 like the native 1920x1080. So there's going to be some distortion.

---

