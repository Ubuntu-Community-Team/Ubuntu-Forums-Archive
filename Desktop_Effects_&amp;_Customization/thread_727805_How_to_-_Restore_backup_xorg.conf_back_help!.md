---
title: "How to - Restore backup xorg.conf back help!"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by srdempster on 2008-03-18
Please can someone give me the kconsole command to restore my old xorg.conf i backed up. Been trying to get 3d on ATI card (lol!) but still no luck!

Steve

---

### Post by sisco311 on 2008-03-18
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```assuming that /etc/X11/xorg.conf-backup is your backup file

---

### Post by Jimmey on 2008-03-18
It depends what the back up is called. To find out, type ```
ls /etc/X11/xorg.conf.*
``` into a terminal.

It'll probably be called xorg.conf.bak.

Whatever it is, type ```
sudo cp /etc/X11/xorg.conf.bak [Or whatever the backup is called] /etc/X11/xorg.conf
```

---

### Post by srdempster on 2008-03-18
I've done it now thanks guys!

---

