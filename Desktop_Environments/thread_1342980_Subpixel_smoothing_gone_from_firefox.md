---
title: "Subpixel smoothing gone from firefox"
date: 2009-12-01
forum: Desktop Environments
---

### Post by Jamesss on 2009-12-01
I just installed systemsettings and kbuildsycoca so I could configure my KDE apps to look the same a my gnome ones and all went well until I restarted firefox 3.5.5 and noticed the font was different. After googling for a bit it seems it's something to do with subpixel smoothing. If I go to System/Preferences/Appearance/Fonts/ and select Best Contrast, all my fonts match the firefox one, but I want to use Subpixel smoothing!

Can anyone help?

---

### Post by Zorael on 2009-12-01
Do you have any **~/.fonts.conf** file? If so, try renaming it (or deleting it outright) and see if it starts listening to GNOME's settings again.

---

### Post by Jamesss on 2009-12-02
perfect - that works!
thank you

---

