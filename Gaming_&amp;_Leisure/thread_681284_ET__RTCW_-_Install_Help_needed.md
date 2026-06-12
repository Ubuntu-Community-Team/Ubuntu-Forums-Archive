---
title: "ET : RTCW - Install Help needed"
date: 2008-01-28
forum: Gaming &amp; Leisure
---

### Post by nipplecrippler on 2008-01-28
Hi  ):P

I have a fresh install of KUBUNTU 7.10 and want to install my favorite game.  I'm following this guide - 
```
http://ubuntuforums.org/showthread.php?t=5246
```

I'm having trouble installing 3D gfx for my 6800GS card, specifically, when I attempt to **Enable Restricted Driver** I see this error message - 
```
**Error - KDE Control Module**
The software source for the package
nvidia-glx-new
is not enabled.
```

Googling this error message links me to this thread - ```
http://ubuntuforums.org/showthread.php?t=582362
```

Which seems to suggest problems with the nvidia-glx-new driver and that perhaps uninstall and reinstall with older nvidia-glx may resolve the problem.

I will continue to search for this answer but any help would be greatly appreciated  :)

---

### Post by luisromangz on 2008-01-29
You may need to enable additional repositories, in the software sources manager application.

---

### Post by nipplecrippler on 2008-01-29
> **luisromangz said:**
> You may need to enable additional repositories, in the software sources manager application.

Yes, thank you luisromangz for replying.

I found in Adept Manager > Manage Repos the setting I needed to enable.

```
Adept Manager > Manage Repos > Kubuntu Software > Proprietary Drivers for Devices (Restricted)
```

After enabling and closing, the Adept Manager downloaded a file.  I was then able to e**enable** the driver via System Settings > Advanced > Restricted Drivers, and after required restart the driver now works.

Thanks.

---

