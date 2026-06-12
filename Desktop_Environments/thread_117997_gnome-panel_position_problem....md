---
title: "gnome-panel position problem..."
date: 2006-01-15
forum: Desktop Environments
---

### Post by dbloom on 2006-01-15
i installed quake 4 the other day and after the first attempt to run, it crashed leaving my screen resolution low. i resized my screen and my gnome panl was hanging mid-screen.  after expanding and un-expanding it, it moved back to the bottom where it belongs.  

oddly, every time i start up now, it launches mid-screen and i have to go through the same exercise again.  

any idea how to fix this?  

here's what it looks like, if i didn't explain it well.
[IMG]http://kouryuu.com/alpha/Screenshot.png[/IMG]

my specs:
Breezy 5.10, with all updates
AthlonXP 2500+
2GB DDR400 ram
60GB hdd
nvidia 6800 video card

---

### Post by dbloom on 2006-01-17
no one's had this problem...?

---

### Post by j_monty10 on 2006-01-17
Have you tried "manually" saving your session after you resize and get your panel where you want it.  You can do this by checking the box when you logout.
Let us know if it works.

---

### Post by dbloom on 2006-01-21
i managed to fix it manually using the Configuration Editor. It was under apps/panel/toplevels and i adjusted the y-position to my screen resolution and it automatically placed it above the bottom panel.  i rebooted and it loaded correctly so it appears to be a permanent solution. :cool: 

hopefully this will help someone else with a similar problem.

--db

---

### Post by anaconda on 2007-09-03
thanks. This helped to solve my problem too. Just hoping that the gnome-panel will be fixed soon. this bug always happens if you change to smaller resolution and back..

---

