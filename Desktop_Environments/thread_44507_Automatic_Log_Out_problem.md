---
title: "Automatic Log Out problem"
date: 2005-06-26
forum: Desktop Environments
---

### Post by hirodotsu on 2005-06-26
Sometimes after I leave my computer for a few hours, I automatically get logged off of Gnome and it goes back to the login screen.  I lose everything that was running before it powered off.  I have it set to do random screen savers without changing anything from the default, besides which screen savers to run.  I'm thinking maybe it's a power-saving thing?  I'm not sure though.  Does anyone know what the problem could be?

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=hirodotsu]Sometimes after I leave my computer for a few hours, I automatically get logged off of Gnome and it goes back to the login screen.  I lose everything that was running before it powered off.  I have it set to do random screen savers without changing anything from the default, besides which screen savers to run.  I'm thinking maybe it's a power-saving thing?  I'm not sure though.  Does anyone know what the problem could be?[/QUOTE]
 Check log files  in /var/log/
It maybe a hardware problem: e.g., if there was power failure, the computer would switch off, then reboot, which would get you back to the login screen

---

