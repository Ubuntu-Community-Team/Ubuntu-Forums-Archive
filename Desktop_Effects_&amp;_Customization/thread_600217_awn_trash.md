---
title: "awn trash"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by Partyboi2 on 2007-11-02
Today there was a update for awn, but since the update my trash can has become a small icon. (screenshot below) Does anyone know how I can get it the same size as the rest of them?

This is what I get when I run awn through the terminal:
```
Screen is composited.
APPLET : /usr/lib/awn/applets/notification-area.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher-3.desktop
LOADED : /home/karl/.config/awn/launchers/awn_launcher-4.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/stack.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_set_qdata_full: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)
/usr/lib/awn/applets/quit-applet/quit-applet.py:72: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  applet = App (awn.uid, awn.orient, awn.height)

(awn-applet-activation:6772): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:6772): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
monitor callback

```
Thanks

---

### Post by Partyboi2 on 2007-11-02
Did anyone else have any problems after the awn updates?

---

### Post by thamood on 2007-11-02
yes me too i have the same problem!!!

---

### Post by thamood on 2007-11-02
hey i found a salution!! i was using a theme so when i tried to change themes everthing went back to normal....just go to the AWN properties and try to change the theme and press "Apply" it should work...

---

### Post by Partyboi2 on 2007-11-02
I tried that and it worked for that session, but if I restart awn it just goes back to being a smaller icon again.

---

### Post by Partyboi2 on 2007-11-02
Just received another update today and its seems to have fixed my trash problem.

---

