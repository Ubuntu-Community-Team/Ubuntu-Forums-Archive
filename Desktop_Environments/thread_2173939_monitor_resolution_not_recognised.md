---
title: "monitor resolution not recognised"
date: 2013-09-12
forum: Desktop Environments
---

### Post by danielsender on 2013-09-12
Hi,

I'm running Ubuntu 12.04LTS on a Dell desktop with a NVIDIA NV31 [GeForce FX 5600 Ultra]. I just attached a recently acquired HP monitor 24" with a native resolution of 1920x1200, connected with the DVI port (no VGA in this monitor). When I open the "Display" section in "System Settings", it shows the word "Laptop" although is not one. And the maximum resolution shown is 1600x1200. If I click on the "Additional Drivers" icon I see that is using the "NVIDIA accelerated graphics driver (version 173) [Recommended]" ("This driver is activated and currently in use"). I tried using the "nvidia-settings" GUI but it didn't display the screen with some excuse of being an old driver configuration. If I run "xrandr" it shows a "default" port instead of DVI and if I try to force "--mode 1920x1200" in xrandr it refuses because is not an allowed resolution.

Can someone help me please?

Thanks in advance.

Daniel

---

### Post by danielsender on 2013-09-13
> **danielsender said:**
> Hi,

I'm running Ubuntu 12.04LTS on a Dell desktop with a NVIDIA NV31 [GeForce FX 5600 Ultra]. I just attached a recently acquired HP monitor 24" with a native resolution of 1920x1200, connected with the DVI port (no VGA in this monitor). When I open the "Display" section in "System Settings", it shows the word "Laptop" although is not one. And the maximum resolution shown is 1600x1200. If I click on the "Additional Drivers" icon I see that is using the "NVIDIA accelerated graphics driver (version 173) [Recommended]" ("This driver is activated and currently in use"). I tried using the "nvidia-settings" GUI but it didn't display the screen with some excuse of being an old driver configuration. If I run "xrandr" it shows a "default" port instead of DVI and if I try to force "--mode 1920x1200" in xrandr it refuses because is not an allowed resolution.

Can someone help me please?

Thanks in advance.

Daniel

Nobody? I tried enabling the 173-updates but nothing changed. I wonder if this is a driver issue or something else. Would the problem disappear if I disable the proprietary driver? Why in the "Display" section of "System Settings" says laptop? Does that mean that the driver does not see the DVI connector and thinks that is a laptop?

Thanks in advance.

---

### Post by danielsender on 2013-09-19
> **danielsender said:**
> Nobody? I tried enabling the 173-updates but nothing changed. I wonder if this is a driver issue or something else. Would the problem disappear if I disable the proprietary driver? Why in the "Display" section of "System Settings" says laptop? Does that mean that the driver does not see the DVI connector and thinks that is a laptop?

Thanks in advance.

Where are the gurus?

---

