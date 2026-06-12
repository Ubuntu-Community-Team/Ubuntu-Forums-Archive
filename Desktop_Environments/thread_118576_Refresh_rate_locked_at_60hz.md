---
title: "Refresh rate locked at 60hz"
date: 2006-01-17
forum: Desktop Environments
---

### Post by danalog on 2006-01-17
I'm having trouble getting my refresh rate up to 72hz which my SONY GDMW 900 monitor supports. It defaults at a headaching 60hz.

I tried editing xorg.conf to have the correct sync rates (H: 30 - 121, V: 48 - 160) but that doesn't do the trick.
I tried creating a special modeline with a modeline utility but with this my resolution goes down instead of staying at 1920x1200. (modeline tool: [http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/))
I tried upgrading my videodrivers, which are now the newest NVIDIA drivers ( 8178 ) on a Club3D 6600GT / agp card. (Getting these drivers to work was hard but I got there :) )

What other things are there to try since I can't find any other info on the forums?

============

Ok I solved the problem using an extra option in xorg.conf. Add the following line to xorg.conf in the Device section:

Option "IgnoreEDID" "true"

---

