---
title: "khotkeys aren't recognized"
date: 2009-05-17
forum: Desktop Environments
---

### Post by paopao on 2009-05-17
I'm running Kubuntu 9.04

When I go to K > System Settings > Keyboard & Mouse > Global Keyboard Shortcuts there is a list of shortcut key groups labeled as KDE component:  At least the kWin component works because I set some handy shortcuts for it; however, the various items in khotkey are not recognized.  For example, to open up Konsole, the shortcut key is ctrl+alt+T, but pressing that does nothing.  I even changed it to something else and it still didn't work.

I'm new to using Linux in general, so I'm not sure what to do.  It seems that having a shortcut key for Konsole would be very nice.

Also, I'm not sure if this is related, but when I boot up, it gives me three errors
ata2.00: xfermode (err_mask=0x4) at times 6.964010, 17.292010 and 27 something.  It still boots and hasn't caused any other problems, so I've been ignoring it.

Also, with alt+F2 to bring up a run applications dialog, is there a way to disable some of the searching/graphics elements of it because sometimes I feel that slows things down.  It would be nice to just type alt+F2 kate without any slowing down.

---

### Post by bhadotia on 2009-06-23
> **paopao said:**
> the various items in khotkey are not recognized.  For example, to open up Konsole, the shortcut key is ctrl+alt+T, but pressing that does nothing.  I even changed it to something else and it still didn't work.

Same problem here. I guess this is some bug in the khotkeys daemon or with the KDE control center module for configuring keyboard shortcuts etc. 
Asfar as I remember this khotkeys for terminal (konsole) etc. used to work for me in KDE 4.1 but after changing its values to some custom combination it stopped working and did not work even if I reverted the settings to their defaults. Here in KDE 4.2 it not working at all:confused:

---

