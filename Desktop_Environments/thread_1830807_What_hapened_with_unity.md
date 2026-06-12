---
title: "What hapened with unity?"
date: 2011-08-22
forum: Desktop Environments
---

### Post by Asgard20032 on 2011-08-22
Before the weekend, when i was booting my computer, it would have booted in unity, but this weekend, i was not here... so i decided to make update and shutdown my computer for the weekend. Now, i come back, when i turn on, it boot under gnome. Is it an update that changed something to how my Ubuntu boot, or it is a bug? I also recently installed ATI binary driver to get opengl header file...

Edit, also checked to log again using other desktop environment:
Ubuntu: No unity
Ubuntu classic: No unity

---

### Post by 3Miro on 2011-08-22
It is possible that the latest kernel update broke the ATI driver. You can try to reinstall the driver from System -> Admin -> Additional Drivers:

1. Go to Additional Drivers and deselect any ATI drivers.
2. Reboot.
3. Go to Additional Drivers and select the ATI driver again.
4. Reboot.

Hopefully this fixes the issue.

---

### Post by Asgard20032 on 2011-08-22
Additional driver: No proprietary driver are in use on this system.


I installed this: ATI binary X.Org driver

When i log in, its alway Gnome interface...

---

