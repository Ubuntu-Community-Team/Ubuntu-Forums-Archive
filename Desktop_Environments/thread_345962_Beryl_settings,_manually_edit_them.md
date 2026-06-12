---
title: "Beryl settings, manually edit them?"
date: 2007-01-25
forum: Desktop Environments
---

### Post by royg1234 on 2007-01-25
I was experimenting with the Beryl settings rendering options, and I chose XGL, and now Beryl's broken.  When I do a ctrl + alt + backspace and log in, the farthest it goes is it shows the desktop background, the panels, clock, and system tray.  But I can't click on anything.

I just want to change the rendering options back to "auto".  Does anyone know how to do this?

---

### Post by aidanr on 2007-01-25
log into a failsafe terminal session and type in the command line

nano ~/.beryl-managerrc

and set platform=0

---

