---
title: "Horrible Graphics!"
date: 2006-08-12
forum: Gaming &amp; Leisure
---

### Post by LaGzo on 2006-08-12
When i play ET:TC I get really bad graphics. Like, when i move the walls overlap other things. I can't see what I'm doing, I can't even see where I'm going. Is this a driver problem??

My system is 
AMD Athlon XP 2600+
Nvidia GeForce MX4000
708 RAM

---

### Post by GuitarHero on 2006-08-13
Well did you install the ndvidia drivers for the card?  It sounds like you didnt.  Ubuntu doesnt auto install the 3d accelerated drivers from nvidia.

---

### Post by syedn on 2006-08-13
look in your xorg configuration (open up your terminal and type 'cat /etc/X11/xorg.conf') and look for your graphics card (e.g. "Device "Nvidia Geforce" etc) under it it should list "Driver".  If it only says 'nv' you don't have 3d acceleration, which helps a great deal/is necessary for gaming.

---

### Post by handy on 2006-08-14
Try [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646"), if you want a painless install of the nVidia closed source drivers, amongst over 45 other choices, which Automatix will install for you...

---

