---
title: "Xorg freezes due to intel graphics driver"
date: 2010-03-06
forum: Desktop Environments
---

### Post by absolutezero1287 on 2010-03-06
I've had trouble on Ubuntu and other Linux distributions with Xorg freezing. It seems that its a problem with the latest intel graphics driver and that I need to roll back to the 2.4 version. I have no problem with using an old driver if its going to be more stable. The trouble came when I actually went ahead and did it. The only package I could find was for Intrepid and I'm using Karmic. That may be where the issue lies but I'm not 100% sure. I did a dpkg -i --force-all and installed the 2.4 version of the intel driver.

After restarting my PC I found that my resolution was messed up and I had no way of fixing it. It was fixed at 600x800 or something like that when it should have been at 1280x1024. 
The display settings couldn't identify my monitor and thus didn't let me adjust the resolution.

I figured that I would have to write an xorg.conf but instead of actually doing that I did some research. Apparently, writing an xorg.conf causes X not to start and messes with terminal emulation. The only thing I haven't tried is compiling the old intel driver from source and installing it. 
Does anyone have any suggestions?

---

### Post by absolutezero1287 on 2010-03-06
Ok, everything seems to be working fine.

I followed the wiki at [this page]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") and everything seems to be working well. If X freezes again I'll make sure to report it.

---

