---
title: "TwinView - fullscreen applications maximize under panel"
date: 2010-11-27
forum: Desktop Environments
---

### Post by Dempf on 2010-11-27
Hello all, I'm new to Kubuntu. Today I hooked up my laptop to an external monitor, and enabled Twinview in the nVidia X Server Settings tool. My right monitor is set as the primary monitor. Both monitors have their position set to absolute. The right monitor is set slightly below the left monitor because that is how the monitors are physically configured (and I find that this TwinView configuration facilitates moving windows between monitors).

As you can see from my attached screenshot, when I maximize a window on the right monitor the window appears *underneath* the panel. This is not default behavior when TwinView is disabled.

My nVidia driver version is 269.19.06 if that helps.

Thanks in advance! :D

Edit:
Found some more information:
[http://ubuntuforums.org/showthread.php?t=1629639](http://ubuntuforums.org/showthread.php?t=1629639)
[http://old.nabble.com/Twinview,-maximized-windows,-panels-td28654066.html](http://old.nabble.com/Twinview,-maximized-windows,-panels-td28654066.html)
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/58977](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/58977)

It appears that the only way that maximizing will work properly is if I move the panel to a location that is not "in between" the two monitors (AKA if the panel is on the right edge of the right monitor or the left edge of the left monitor). This makes managing windows on a dual monitor setup somewhat frustrating for me.

Do you guys think that I should file a separate bug against KWin in apport?

---

