---
title: "how to get usplash working for 1024x600?"
date: 2009-05-02
forum: General Help
---

### Post by jon.reeve on 2009-05-02
Usplash has never really displayed correctly on my 1024x600 screen (MSI Wind), but since I upgraded to Jaunty it's gotten worse. It's all warped-looking and small. Does anyone know how to fix this? My /etc/usplash.conf file looks correct: 

xres=1024
yres=600

but I can't seem to find the correct "vga=" line that will make this work. 

Any ideas?

---

### Post by dcstar on 2009-05-02
> **jon.reeve said:**
> Usplash has never really displayed correctly on my 1024x600 screen (MSI Wind), but since I upgraded to Jaunty it's gotten worse. It's all warped-looking and small. Does anyone know how to fix this? My /etc/usplash.conf file looks correct: 

xres=1024
yres=600

but I can't seem to find the correct "vga=" line that will make this work. 

Any ideas?

There are only a limited amount of resolutions available, it is a VESA hardware limitation and there is nothing anyone can do about it.

---

