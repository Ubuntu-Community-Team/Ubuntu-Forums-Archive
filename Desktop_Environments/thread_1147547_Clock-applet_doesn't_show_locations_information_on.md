---
title: "Clock-applet doesn't show locations information on mouse hover in Ubuntu 9.10"
date: 2009-05-03
forum: Desktop Environments
---

### Post by gcha on 2009-05-03
Hi,

I recently upgraded to Ubuntu 9.10 and excepted minor problems quickly solved ( Amarok stopped working because phonon-backend-xine missing, and vlc showing up in two windows) there is only one thing that bothers me:

In Ubuntu 8.10, you could hover the mouse over the locations set, and get the sunrise/sunset time, the temperature, the windspeed. Now the information is unavailable, however, it still fetches the information since the icon next to the location is either a sun, clouds, rain, or a moon. 

Is this behaviour confirmed by other users? 
Should I fill a bug for that?
Who exactly is responsible of that, Gnome?

Thanks.

---

### Post by PacSci on 2009-05-03
I've confirmed that the hovering weather functionality isn't available in Jaunty, either.

If it is a bug, I'd go to GNOME about it, since they're the ones who write the Clock applet.

---

### Post by gcha on 2009-05-04
I've reported the bug :

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/371770](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/371770)

---

### Post by gcha on 2009-05-06
At the end, I changed the theme and it started working again. 

I guess it was an interference between the theme and the gnoma panel applet.

---

