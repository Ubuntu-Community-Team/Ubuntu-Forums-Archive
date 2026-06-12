---
title: "Xubuntu and nautilus"
date: 2008-04-03
forum: Desktop Environments
---

### Post by avantgardaclue on 2008-04-03
Hi guys.... last October i installed ubuntu 7.10. Then I downloaded the xubuntu desktop. I have been flitting between gnome and xfce as my mood takes me. However on my rather elderly machine i have come to the conclusion that i prefer xubuntu, it appears to be faster.

For file browsing Thunar boots up in a fraction of the time that nautilus does, however nautilus is fundamentally more powerful that Thunar so it's nice to occasionally boot that up. The other day in fact i was looking at the latest batch of pics off my digital camera with a view to deleting the duff shots. Nautilus allows me to resize the thumbnail icons pretty large which was a boon when it comes to choosing the doomed shots. Worked beautifully!

However when i had finished i shut down nautilus and returned to the desktop and I had a Gnome desktop, with file thumbnails, background etc, along with the XFCE tool bars top and bottom.

In desktop settings the 'allow XFCE to manage the desktop' had become unticked.

Simply re-ticking brings back the xububtu desktop but very irritating. However it does appear, quite randomly, to go back to gnome.

Any advice gratefully received... thanks

---

### Post by kpkeerthi on 2008-04-03
It is advisable to start nautilus using ```
nautilus --no-desktop
``` if you do not wish it to take control of your other XFWM's desktop.

---

### Post by avantgardaclue on 2008-04-03
> **kpkeerthi said:**
> It is advisable to start nautilus using ```
nautilus --no-desktop
``` if you do not wish it to take control of your other XFWM's desktop.

Added that to the code in my launcher and seams to work... thanks!!

---

