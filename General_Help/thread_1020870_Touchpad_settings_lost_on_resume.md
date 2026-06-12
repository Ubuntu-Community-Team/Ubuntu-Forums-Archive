---
title: "Touchpad settings lost on resume"
date: 2008-12-24
forum: General Help
---

### Post by thekidder on 2008-12-24
I have a script configured to run on KDE startup (located in .kde/Autostart) that runs synclient a few time to adjust some touchpad settings (acceleration, etc). Up to 8.10, this worked fine. When I upgraded I had to deal with the changes in Xorg: take Options SHMConfig "on" out of xorg.conf and add it to another file (I think it was somewhere in HAL). This worked, except for one point - after resuming from suspend I had to run the script again. I tried symlinking the script to /etc/acpi/resume.d/, but this did nothing. Any suggestions?

---

### Post by thekidder on 2008-12-26
bump.

Any ideas? This is the only downside I've had with 8.10 yet.

---

