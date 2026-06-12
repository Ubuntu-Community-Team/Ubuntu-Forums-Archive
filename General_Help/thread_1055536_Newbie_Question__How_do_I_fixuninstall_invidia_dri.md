---
title: "Newbie Question:  How do I fix/uninstall invidia driver without display working?"
date: 2009-01-30
forum: General Help
---

### Post by GeneralTso on 2009-01-30
Hiya,

Sorry for the newbie question, but I googled everywhere before posting and I couldn't find anything helpful.  

Today I installed Ubuntu 10.8 and everything worked great.  When prompted, I activated the restricted invidia display driver.  After the reboot, I got the initial splash screen and then the screen went blank.  Then the monitor displayed a "Settings outside of range" error.  The new driver was probably trying to display a refresh rate too high for my monitor.

It played the startup drum beat and then the welcome music after I typed my username/password, so it isn't locked up...but I can't see anything except for the "outside of range" error so I can't figure out how to change the settings.

Is there a way that I can get it to boot using the default monitor drivers so I can see what I'm doing while adjusting the display settings?  Any other thoughts on resolving this would be great!

Thanks!

Jeff

---

### Post by taurus on 2009-01-30
Reboot your machine and at the GRUB menu, use the arrow to move down to the recovery mode and boot from it.  Then, pick the fix X server option (xfix) at the menu and see if that fixes or resets your driver when you reboot back with the normal kernel.

---

### Post by GeneralTso on 2009-01-31
That did the trick...Thanks Taurus!

Jeff

> **taurus said:**
> Reboot your machine and at the GRUB menu, use the arrow to move down to the recovery mode and boot from it.  Then, pick the fix X server option (xfix) at the menu and see if that fixes or resets your driver when you reboot back with the normal kernel.

---

