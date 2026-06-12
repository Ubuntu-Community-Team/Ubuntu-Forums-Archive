---
title: "re-installation from HD on Inspiron mini 9"
date: 2009-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dr Bob The Chameleon on 2009-07-13
I've come to the conclusion my keyboard shutout problem is likely unsortable and have resigned myself to re-installing- I have a complete backup of my files.
Looking at the Dell Ubuntu 8.04 O/S reinstalation page it says to reinstall from HD press ESC soon after the Dell logo appears. This should produce the GRUB menu, except, it doesn't. I can get into setup etc so I know the keyboard is OK at that point but no GRUB. What am I missing?
Scott

---

### Post by ugm6hr on 2009-07-16
Where did you read that?

The default Dell Ubuntu for the Mini is set up to try and dissuade access to Grub.  To get there, you need to press Escape rapidly at that point, and hope for the best.  The alternative is to edit /boot/grub/menu.lst to change the 0 to a 1 in the "timeout 0" line near the top, then reboot and press Escape at the relevant time (after the Dell logo).

Unfortunately, I suspect this will in no way help you to reinstall, unless Dell's configuration of their Mini with HD is significantly different to the SD version (which is possible, since HD space is at less of a premium).

If I am correct, and there is no reinstallation option in Grub, you will need to reinstall from either an external DVD, or a USB drive.  Uncertain whether the latter can be used with the Dell Ubuntu; I would just recommend the Netbook Remix 9.04 for simplicity.

---

