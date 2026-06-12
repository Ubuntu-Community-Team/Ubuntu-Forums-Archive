---
title: "!!!! xorg - no screens?? cant get back in"
date: 2007-04-30
forum: Desktop Environments
---

### Post by norton1 on 2007-04-30
hi - i've foolishly gone a changed my xorg.conf file.
now when i rebooted it comes up with 'no screen' and all i can do is look at the xorg error messages and then i have to turn off the computer - how can i get back to my xorg.conf file to fix it??

i guess i just need to run the sudo dpkg -reconfigure -phigh xserver-xorg
but how can i get into terminal from grub (i also edited grub file so it just shows ubuntu / winxp - no recovery modes!

i guess i shuld stop editing these files eh

please help - i promise i'll never do anything stupid again

---

### Post by taurus on 2007-04-30
Boot into recovery mode from GRUB menu (may need to press Esc to bring up the menu when you first turn on your computer) and reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
-or-
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by norton1 on 2007-04-30
thanks for that - i managed to get it going again by booting into windows and editing the xorg.conf file with notepad - then rebooting into windows - strange thing is my AVN manager is working better now?

phew...

---

### Post by norton1 on 2007-04-30
sorry, i mean rebooting into ubuntu!!!

---

