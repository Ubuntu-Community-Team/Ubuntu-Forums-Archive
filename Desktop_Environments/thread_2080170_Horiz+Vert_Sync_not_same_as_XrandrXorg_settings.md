---
title: "Horiz+Vert Sync not same as Xrandr/Xorg settings"
date: 2012-11-03
forum: Desktop Environments
---

### Post by xenginebuilder on 2012-11-03
I have been fighting a problem with a black screen/out of range problem with 2 different LCD monitors. Before I start attaching or posting log files and config settings, what appears to happen is that the output from the video card to the monitor is somehow being driven to a different H and V sync value than the system settings would suggest, for instance instead of 1280x1024 60hz (default native timing for Monitor0) the actual Vertical sync is 65.2, which one monitor will handle even though it is not a valid EDID mode. Any changes to any other sync using the settings manager or xrandr triggers the "out of range" message and a blank screen.
The other monitor is 1600x1200 native, goes blank sometime around the handoff to the nouveau fb during boot, there is no setting or resolution that will make this monitor work except to boot using nomodeset. This is also the same for the 1280x1024 monitor, where the vertical sync changes from 60 to 65 sometime around the handoff, but that monitor can handle it.
Otherwise, the nouveau driver works perfect for what I need, no tearing, good performance for desktop functions/programs, can watch full screen videos without problems.
Every time I have installed the proprietary nvidia drivers (tried in 9.04-9.10-10.04) with 2 different Nvidia cards, they have been buggy and cause system freezes, and have had to default to the "nv" driver just to get stability.  I will not try the nvidia blob in 12.04 as experience says both installation and inevitable removal will involve many wasted hours that I don't have to spare.
Both monitors work perfectly in dual head or single mode with Win2k using nvidia driver, and report the correct H+V timings at native resolutions,  so I believe the hardware is not faulty. 

The basics:
Linux version 3.2.0-33-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52-Ubuntu SMP Thu Oct 18 16:19:45 UTC 2012
Ubuntu 12.04.1 LTS
01:00.0 VGA compatible controller: NVIDIA Corporation NV31 [GeForce FX 5600] (rev a1)
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV31
OpenGL version string: 1.5 Mesa 8.0.4

No errors in xorg.0.log

Appreciate any help or ideas on how to resolve this.

---

