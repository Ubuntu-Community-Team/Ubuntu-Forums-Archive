---
title: "problem installing NVIDIA driver in 9.04"
date: 2009-05-16
forum: General Help
---

### Post by marenum on 2009-05-16
I recently updated to 9.04. When I try to install the NVIDIA accelerated graphics driver (version 180), i get this error message when I restart:

"Ubuntu is running in low graphics mode. 

The following error was encountered. You may need to upgrade your configuration to fix this.

(EE) NVIDIA (0) failed to load the NVIDIA kernel module!
(EE) NVIDIA (0) ***aborting***
(EE) Screens (s) found, but none have usuable configuration"

I can use the version 173 driver, but I could use 180 fine before I updateed. My graphics card is a GeForce 8600 GT. Any ideas?

---

### Post by DeMus on 2009-05-16
> **marenum said:**
> I recently updated to 9.04. When I try to install the NVIDIA accelerated graphics driver (version 180), i get this error message when I restart:

"Ubuntu is running in low graphics mode. 

The following error was encountered. You may need to upgrade your configuration to fix this.

(EE) NVIDIA (0) failed to load the NVIDIA kernel module!
(EE) NVIDIA (0) ***aborting***
(EE) Screens (s) found, but none have usuable configuration"

I can use the version 173 driver, but I could use 180 fine before I updateed. My graphics card is a GeForce 8600 GT. Any ideas?

You updated to 9.04 or did you do a fresh install?
When you updated, which driver were you using before the update?
How did you install the accelerated driver? Did you use System - Administration - Hardware drivers? Or did you download a file from the nVidia website?

---

### Post by marenum on 2009-05-16
I updated, not fresh install. I believe I was using the version 180 driver before the update.I did use System - Administration - Hardware drivers to install the driver.

---

### Post by DeMus on 2009-05-16
> **marenum said:**
> I updated, not fresh install. I believe I was using the version 180 driver before the update.I did use System - Administration - Hardware drivers to install the driver.

In System - Administration do you have an item called nVidia X Server Settings? If so, when you start it what does it say about the settings you have at this moment?
Or is it impossible to start it at all?
What happens when you uninstall the hardware driver, the way to installed it? Do you get your high resolution then?

All I did after installing Jaunty was click the hardware drivers and install the proprietary driver, rebooted and that's it. I have a 8500GT, which can not be that different from your card. Why there have to be such big differences in installation the cards, I don't know. Many people suffer from it, and others (like me-this time) had no problem at all.

---

### Post by marenum on 2009-05-16
It runs fine using the (version 173) driver. I get my full resolution, but no screen effects.

---

