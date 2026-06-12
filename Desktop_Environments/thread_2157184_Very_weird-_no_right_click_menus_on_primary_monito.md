---
title: "Very weird- no right click menus on primary monitor"
date: 2013-06-24
forum: Desktop Environments
---

### Post by cincinnatus13 on 2013-06-24
Using Ubuntu Gnome 13.04 with the 3.8 repo.
All I did was update to the latest kernel I believe and now for some reason right clicking doesn't work on my primary monitor.
For example, I have spotify (and it's the same for other programs) on the primary monitor and can't right click any menus. It just sits there.
I move the program to my secondary monitor though and it works just fine.

What could cause something like this? I'm kind of at a loss.

---

### Post by cincinnatus13 on 2013-06-25
Easy enough- reset the X server. Not sure what got messed with but a simple sudo sh /etc/X11/Xreset and reboot did the trick.

---

