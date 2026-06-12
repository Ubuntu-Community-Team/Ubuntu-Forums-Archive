---
title: "How do I change the monitor settings?"
date: 2009-03-12
forum: General Help
---

### Post by robofighter on 2009-03-12
I changed my screen resolution settings the other day to allow dual monitors.

But now all the icons and menus are all the monitors that is no longer plugged in my laptop. I have tried to turn off the second monitor setting when I got home, but It apparently started back up again on that setting, when I was at class today when I booted up the machine.

---

### Post by Yellow Pasque on 2009-03-12
Heh, your post doesn't make much sense to me. What kind of video card do you have and how did you change monitor resolutions?

Post your /etc/X11/xorg.conf and /var/log/Xorg.0.log

---

### Post by robofighter on 2009-03-12
sorry, but my computer seems to set up for dual monitors when only one monitor is on and I do not have a second monitor plugged in.

the problem is that all the icons and panels are all set for the secondary monitor that is not plugged in. I can see them for a brief second when I change the desktops panels. It is acting as if my secondary external monitor is the primary monitor with my laptop monitor as the secondary monitor.

I can not figure out how to get to screen resolution page to change the settings back to normal. As I said be before all the panel somehow got set to the secondary monitor that never plugged, so the panels are never shown.

Does anyone know where in the file system I can access the screen resolution program.

Also I am using an Intel express 945

---

### Post by Yellow Pasque on 2009-03-12
Just boot to recovery mode (press Esc after your system POST's to access the GRUB menu). When offered a menu, select xfix.

---

