---
title: "Compiz Emereld"
date: 2008-06-23
forum: Desktop Environments
---

### Post by StephanG on 2008-06-23
Hi everybody,
I'm using kubuntu 8.04, and for some reason, when compiz is activated, there are no emerald window borders.  How can I restore the emerald borders?  Kwin has no problems, and the emerald manager makes no difference.  Besides the missing borders, everything seems fine.  Thanks for your input :)

---

### Post by argail1980 on 2008-06-23
nvidia card?

---

### Post by Sub101 on 2008-06-23
Try ```
emerald --replace
``` in the terminal. 

If it works then add the command to your startup programs.

EDIT: Also check to see you have visual effects enabled.

---

### Post by ad_267 on 2008-06-23
In the compizconfig-settings-manager make sure the Window Decoration plugin is enabled and the Window Decoration command set to "emerald --replace"

---

### Post by StephanG on 2008-06-23
Thanks,
I've tried emerald --replace and then it gives the error message:
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'

Also, window decorations are enabled.  Changed command to emerald --replace, made no noticeable difference.

---

### Post by StephanG on 2008-06-23
Oh, and also yes it is a nVidia card. Geforce 6600.

---

### Post by StephanG on 2008-06-24
***bump***

---

### Post by ad_267 on 2008-06-24
Does that file exist?

Can you post the output of:
```
cat /etc/qt3/qt_plugins_3.3rc
ls -l /etc/qt3 | grep qt_plugins_3.3rc
```

I've got no idea what the error means but just trying to get more info. I have that file and I'm using gnome so I guess you should have it using KDE. Are you using KDE4 or KDE3?

---

