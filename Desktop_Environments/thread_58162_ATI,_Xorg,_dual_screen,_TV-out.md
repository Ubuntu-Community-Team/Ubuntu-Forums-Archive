---
title: "ATI, Xorg, dual screen, TV-out"
date: 2005-08-19
forum: Desktop Environments
---

### Post by Morrigu on 2005-08-19
I'm running Ubuntu 5.04, and have the latest ATI drivers installed.

I'm looking for tips how to configure the following setup : 

With my ATI Radeon 9600 Pro I'd like to use dual screen as extended desktop. So far I haven't been able to configure Xorg so that this would work, I just get clone mode. I'd also like to have some easy and fast way to switch my other screen to display on tv-out instead on secondary monitor. ATI can only use 2 different displays, and at the moment in Windows XP I need to use the display control panel to switch from DVI + VGA to DVI + TV-Out.

Also I can't seem to get hardware 3D acceleration, how do I enable it?

Thanks for help!

---

### Post by Morrigu on 2005-08-21
Up

---

### Post by tag on 2005-08-21
This is strange. ATI apparently released their most recent driver (8.16.20) on 2005.8.18 and claimed that some of these dual screen issues were tackled in this release. Are you sure you downloaded the right version? See [http://www2.ati.com/drivers/linux/linux_8.16.20.html](http://www2.ati.com/drivers/linux/linux_8.16.20.html) for instructions on how to download/install/configure the driver.

See [http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557) for instructions on how to configure Xorg to use 3d acceleration (keep in mind that the ati drivers in the ubuntu repository have not yet been updated).

---

