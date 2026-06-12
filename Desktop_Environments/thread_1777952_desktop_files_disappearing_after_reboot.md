---
title: "desktop files disappearing after reboot"
date: 2011-06-08
forum: Desktop Environments
---

### Post by Z.K. on 2011-06-08
I setup the chromium browser to come up in kiosk mode in the startup applications and after rebooting it does not come up in kiosk mode and the startup application entry is now gone.  I have several machines and though they all have the exact same hardware and software, some lose the startup application entry on reboot and some do not.

I was wondering if anyone might know what is going on and what might be the fix for this.  I don't think it is a chromium problem, but I am positive.

The command I use for the chromium browser is:
```
chromium-browser --kiosk
```

---

### Post by Z.K. on 2011-06-08
> **Z.K. said:**
> I setup the chromium browser to come up in kiosk mode in the startup applications and after rebooting it does not come up in kiosk mode and the startup application entry is now gone.  I have several machines and though they all have the exact same hardware and software, some lose the startup application entry on reboot and some do not.

I was wondering if anyone might know what is going on and what might be the fix for this.  I don't think it is a chromium problem, but I am positive.

The command I use for the chromium browser is:
```
chromium-browser --kiosk
```

Okay, well I found a solution.  In the .profile file in the user's home directory, I put```
chromium-browser --kiosk  &
``` at the end of the file.  Now, it brings up chromium every time.

Of course it does not address the problem as to why the desktop file keeps being deleted upon reboot.  It is the best I can do at the moment though.

:)

---

