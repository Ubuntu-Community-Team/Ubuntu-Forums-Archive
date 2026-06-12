---
title: "Screen Resolution"
date: 2009-03-16
forum: General Help
---

### Post by Mila on 2009-03-16
Over the weekend my [s]idiot[/s] little brother tried installing and running some games in Wine. In the process he managed to set my screen resolution down to 1024x768. (It used to be at 1280x800.) Now when I try to set it back to 1280x800 (System > Control Panel > Monitor Resolution), it only partially resizes, leaving me with a black border. When I then set it back to 1024x768 and click "Apply", my computer shuts down.

Anybody have any ideas on how to reset my monitor resolution? This 1024x768 business is driving me a little nuts.

I'm running Ubuntu 8.10.

---

### Post by anlag on 2009-03-16
Try

sudo dpkg-reconfigure xserver-xorg

and follow instructions on screen. It will, perhaps obviously, reconfigure your X server which may be enough to get rid of the problem.

---

### Post by Mila on 2009-03-16
No, that didn't do it. It still gives me the funky black border on the 1280x800 resolution, and crashed when reseting it to 1024x768.

---

### Post by Eamon1 on 2009-03-25
I had a similar problem.

xrandr -s 0

fixed it for me.


For more info check the wine faq at 
[http://wiki.winehq.org/FAQ#head-acb200594b5bcd19722faf6fd34b60cc9c2f237b](http://wiki.winehq.org/FAQ#head-acb200594b5bcd19722faf6fd34b60cc9c2f237b)

---

