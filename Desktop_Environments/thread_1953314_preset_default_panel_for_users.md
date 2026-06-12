---
title: "preset default panel for users"
date: 2012-04-06
forum: Desktop Environments
---

### Post by xris_xcess on 2012-04-06
Hi...

I've implemented a custom setup in a school with xfce4 and ubuntu minimal. All panels are preset and locked, but the new users that login for the first time get asked if they wish to use the default or an empty panel.

Does anyone know how to prevent this and enforce the preset "default" panel automatically?

I have searched around ( [http://mail.xfce.org/pipermail/xfce4-commits/2011-April/018751.html](http://mail.xfce.org/pipermail/xfce4-commits/2011-April/018751.html) ) and found some info about setting a variable (XFCE_PANEL_MIGRATE_DEFAULT), but there no explanation of where to set this. Is it like a regular bash variable? Could I set it in rc.local or xinitrc?

---

### Post by Paddy Landau on 2012-04-06
Try setting it in the file /etc/environment. The format would be
```
XFCE_PANEL_MIGRATE_DEFAULT='x'
```(Replace 'x' with whatever it is supposed to be.)

---

### Post by muzzol on 2012-05-09
hi, 

i'm with similar proble, i want to avoid message that asks for emtpy or default panel.

how can i provide my own xfce setup?

---

