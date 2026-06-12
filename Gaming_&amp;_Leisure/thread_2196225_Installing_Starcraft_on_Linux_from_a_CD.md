---
title: "Installing Starcraft on Linux from a CD"
date: 2013-12-28
forum: Gaming &amp; Leisure
---

### Post by blake4 on 2013-12-28
I have the **Starcraft CD**, and when I load it, it works fine. Until I login -- then it just crashes. Aside from lowering the graphics or resolution, I knew someone who said there was something you do before hand and it should eliminate the problem. Does anyone know a successful way to run Starcraft on Linux (Ubuntu) without it crashing after login? I'm not in touch with that person, so aside from graphic changes, not sure what he did because I remember he was able to find a way.

---

### Post by Bashing-om on 2013-12-28
blake4; Hi ! 

Graphics related ? Not knowing your graphics card, this maybe nothing more than a shot in the dark !
For Nvidia and ATI graphics cards;
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is - with "nomodeset" - OK at this point. ->
Additional Drivers, location varies depending on the version, ->locate the Additional Drivers utility and install the recommended driver.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by oldrocker99 on 2013-12-28
Very good advice!

---

### Post by blake4 on 2013-12-28
Thanks for the help!

---

### Post by Bashing-om on 2013-12-28
blake4; That is why we are here, no problem.

Be aware using "nomodeset" is not generally considered a good long term solution, as kernel mode setting is disabled.
You need to get a driver installed.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

