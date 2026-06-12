---
title: "BSOD screen saver missing after upgrade to DD"
date: 2006-06-05
forum: Desktop Environments
---

### Post by frjack on 2006-06-05
Since my upgrade to 6.06 the BSOD screensaver apears to have vanished. 

Anyone know how to get it back?

i noticed that the preferances now goes to a gnome screensaver manager not the xscreensaver one. I installed xscreensaver interface instead but it shows all the screensavers that the gnome one does. and has many greyed out including bsod saying it is not installed. Can anyone tell me what package is needed to get it back

--Steve

---

### Post by oyvindaa on 2006-06-05
Perhaps it'll help if you remove the gnome-screensaver.

```
sudo apt-get remove gnome-screensaver
```

---

### Post by frjack on 2006-06-05
Found it. I needed to install xscreensaver-data-extra that added the bsod to the gnome interface.

--Steve

---

### Post by oyvindaa on 2006-06-05
Cool. Glad you sorted it out mate.

---

