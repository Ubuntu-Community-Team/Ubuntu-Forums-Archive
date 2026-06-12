---
title: "How do I revert to a previous version of a driver?"
date: 2009-02-08
forum: General Help
---

### Post by lingenfr on 2009-02-08
I have a Toshiba Libretto U100. When I installed Intrepid (32-bit), the video was great. After upgrade the screen is wrapped vertically and I can't fix it. The culprit seems to be the latest intel video driver. I would like to reinstall the version of the intel driver that came on the Intrepid installation CD. I don't want to do anymore troubleshooting. I have been at that long enough. I just want to reinstall a working driver (or try that). I would appreciate any assistance. Thanks.

---

### Post by drs305 on 2009-02-08
If the drivers were installed normally, you may have the older driver still listed in System > Administration > Hardware Drivers. If so, select the older driver and "Activate".

For normal packages in synaptic, there is an option under "Package" to *force* a version of a particular package. I don't know if it works the same way for video drivers. You might be able to do it from here if the older driver is still listed, although the first option is preferable.

---

### Post by lingenfr on 2009-02-08
They were installed as part of the initial installation and upgraded via synaptic updater. I checked under System>Administration>Hardware Drivers, but the only driver listed there was for my Atheros wireless adapter.

So, I went into Synaptic and found xserver-xorg-video-intel. The installed version was 10.3. I highlighted that package and went to the menu Package>Force Version and selected version 10 and applied. I closed out and prevented it from updating. I rebooted and... YEAH! No more vertical wrap. Thanks for the prompt response.

---

