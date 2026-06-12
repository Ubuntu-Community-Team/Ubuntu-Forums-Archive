---
title: "AWN Applets are white lines"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by bpickel on 2007-10-24
When I add my Bling Switcher applets I get a white line and no applet. The odd thing is that I have this installed on another machine and it is the clock applet that does this. Can anyone help. Has anyone seen this before

---

### Post by TedGarvin on 2007-10-27
I have the same problem.  Several of my icons appear as white lines.  No one seems to know the answer.  It may be a bug.

---

### Post by pt123 on 2007-10-27
start AWN through a terminal window then you will see the error messages whenever you get these white lines.

---

### Post by TedGarvin on 2007-10-27
> **pt123 said:**
> start AWN through a terminal window then you will see the error messages whenever you get these white lines.
Thanks.  I was running a notification area in a gnome panel and that prevented it from showing up in the awn dock.  Once I removed it, I was fine.  Also had to install some modules ( alsaaudio-python module and the python-gconf) to get the volume control working.  But something else is very wrong.   I get:
```
Screen is composited.
APPLET : /usr/lib/awn/applets/main-menu.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
LOADED : /home/pjh/.config/awn/launchers/awn_launcher-1.desktop
LOADED : /home/pjh/.config/awn/launchers/awn_launcher-2.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/trash.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/quit-applet.desktop
APPLET : /usr/lib/awn/applets/notification-area.desktop
APPLET : /usr/lib/awn/applets/volume-control.desktop

(awn-applet-activation:26737): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

(awn-applet-activation:26737): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
Traceback (most recent call last):
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 129, in <module>
    applet = App (awn.uid, awn.orient, awn.height)
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 32, in __init__
    self.ObjSwitcher.DrawSwitcher(self)
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 86, in DrawSwitcher
    icon = self.GenerateBackgroundThumbPixbuf(self.GetActiveWorkspaceNumber(),applet.get_height())
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 93, in GenerateBackgroundThumbPixbuf
    self.switcher.draw_on_square(ct2, n, h)
  File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line 165, in draw_on_square
    self.draw_complete_thumb(context, side, thumbheight, 0, 0, n, True, True)
  File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line 100, in draw_complete_thumb
    self.draw_retangle_with_background_over(context, w, h, x, y,n, squared)
  File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line 111, in draw_retangle_with_background_over
    pixbuf = self.get_pixbuf_background(w, h,squared)
  File "/usr/lib/awn/applets/BlingSwitcher/CairoWidgets_BlingSwitcher.py", line 232, in get_pixbuf_background
    self.bgpixbuf_for_squared = gtk.gdk.pixbuf_new_from_file(url2)
gobject.GError: Failed to load image '/home/pjh/wallpaper.png': Fatal error in PNG image file: too many length or distance symbols
The gconf key is empty.

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (awn-applet-activation:26737): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:26735): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
Creating new applet :None uid:None
Creating new applet :/usr/local/lib/awn/applets/switcher.desktop uid:1193527498

** (awn-applet-activation:26862): WARNING **: This desktop file does not exist None

 
```

Looking at that, does anything seem to jump out at anyone?

---

### Post by chimby on 2007-10-29
Yes, I have the same problem with the white lines. Most of my launchers and applets appear as white lines and are mostly useless. I am searching the awn forums too.

---

### Post by jsully1 on 2007-10-29
Same problem here.
edit - launching awn from a terminal, when I try to add several applets I get "ImportError: No module named awn".

---

### Post by TedGarvin on 2007-10-29
Did you guys try to run in it in the terminal?

---

### Post by blastfm on 2007-11-05
> **TedGarvin said:**
> Thanks.  I was running a notification area in a gnome panel and that prevented it from showing up in the awn dock.  Once I removed it, I was fine.  

This one helped me. Thanks

---

### Post by weezerisrock on 2007-11-06
I am also having this problem, I've removed the windows list from my gnome panel, and everything shows up ok in awn, even my shortcuts however, my applets are not showing up.  None of them except the taskmanager.  They all show up as white lines.

Here is my code when I run it in terminal

```
Screen is composited.
LOADED : /home/mckayr/.config/awn/launchers/awn_launcher-1.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/PySwitcher.desktop
APPLET : /usr/lib/awn/applets/weather.desktop

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:11089): Wnck-WARNING **: Unhandled action type (nil)

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed

** (avant-window-navigator:11089): CRITICAL **: awn_draw_icons: assertion `x >= 0 && x < fx->icon_width && w-x > 0 && w-x <= fx->icon_width && y >= 0 && x < fx->icon_height && h-y > 0 && h-y <= fx->icon_height' failed
Traceback (most recent call last):
  File "/usr/lib/awn/applets/BlingSwitcher/PySwitcher.py", line 8, in <module>
    import awn
ImportError: No module named awn
Traceback (most recent call last):
  File "/usr/lib/awn/applets/weather/weather.py", line 30, in <module>
    import awn
ImportError: No module named awn

```

I imagine I have to be missing something for that many warnings and criticals lol, can anyone help me out?

Thanks

---

### Post by Jonie on 2007-11-20
You are missing dependency which is not automatically resolved, if you use trevino repo. Installing python-libawn0 via Synaptic will do the trick.

---

