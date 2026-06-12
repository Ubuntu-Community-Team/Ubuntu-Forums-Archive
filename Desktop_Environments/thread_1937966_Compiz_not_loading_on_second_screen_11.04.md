---
title: "Compiz not loading on second screen 11.04"
date: 2012-03-08
forum: Desktop Environments
---

### Post by devosion on 2012-03-08
After alot of work trying to get gnome classic and compiz to work together with dual monitors it seems that I keep running into new errors. I have dual monitors working with two x screens, and no xinerama. This works just fine, and after trying a work around to enable the desktop cube by reverting to an older version of compiz I started having a problem where my main x screen was occupied by an unusable purple screen. After removing the older packages, and muddling through the current compiz packages to gain two working x screen again I now have a problem where my main screen loads correctly, but the other seems to be completely unusable. Within my main screen composite is loading, and all window functionality is usable and changeable via the ccsm. But in the second screen all windows appear without a menu bar, and I can't even input text into input boxes, or close the windows. Any help would be appreciated. 

It may also be of note that the problem persists even with composite disabled.

SOLVED

Managed to get compiz and composite working by enabling twinview in nvidia settings manager. Apparently compiz can only read the information on the second screen, when using an nvidia card, by doing this. Compositing works now too.

---

