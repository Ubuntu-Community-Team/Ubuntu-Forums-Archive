---
title: "Tray Icon help"
date: 2009-06-01
forum: Desktop Environments
---

### Post by BigMoeW on 2009-06-01
I recently installed a dock and turned the notification area off, but I still want to see my wireless tray icon. So, does anyone know either how to make wicd tray icon appear w/o the notification area, or if thats not possible with wicd, a wireless manager that can show its tray icon w/o the notification area?

Ubuntu 9.10 (Juanty)
GNOME
Wicd 1.5.9

---

### Post by imdano on 2009-06-01
You can use ```
wicd-client -n
```to display the wicd GUI without the tray icon, but there isn't a way to display the tray icon without a notification area.

---

### Post by BigMoeW on 2009-06-01
Thanks. Do you know of another wireless manager who's tray icon can be displayed w/o the notification area?

---

### Post by ontadimanamana on 2009-06-01
add wicd to panel

---

### Post by BigMoeW on 2009-06-01
The panel only adds an app launcher, and when I put 'wcid' it only launches the gui, not the tray icon (the one that shows the connectivity bars). I'm looking for tray.py on my system, but I can't find it.

---

### Post by dBuster on 2009-06-01
Is there not a screenlet that you can add to the app launcher?  I know there is a screenlet that shows the wifi connectivity signal strength.  Or search for a wicd screenlet type app for your launcher.

---

### Post by BigMoeW on 2009-06-01
> **dBuster said:**
> Is there not a screenlet that you can add to the app launcher?  I know there is a screenlet that shows the wifi connectivity signal strength.  Or search for a wicd screenlet type app for your launcher.

Thanks, the screenlet worked out great.

---

