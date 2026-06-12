---
title: "AWN only launches from terminal"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by SkyCapitan on 2007-11-07
I just installed awn-curves from this HOWTO:

[http://ubuntuforums.org/showthread.php?t=572019]("http://ubuntuforums.org/showthread.php?t=572019")

When i run "avant-window-navigator" from the terminal, everything works fine - I can access preferences, add applets, etc.  But when I ALT+F2 and type the same, nothing happens. Likewise, the AWN entry in my K-Menu does nothing either.

I'm running Kubuntu 7.10, here's the terminal output when i run awn:
[INDENT]-desktop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/lib/awn/applets/awn-system-monitor.desktop
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/filebrowser.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
APPLET : /usr/lib/awn/applets/separator.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/kde/adept_manager.desktop
LOADED : /usr/share/applications/kde/konsole.desktop
LOADED : /usr/share/applications/kde/ktorrent.desktop
LOADED : /usr/share/applications/kde/d3lphin.desktop
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/showdesktop.desktop
APPLET : /usr/lib/awn/applets/trash.desktop

(awn-applet-activation:7811): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
return

(awn-applet-activation:7811): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
return
return

[/INDENT]

But everything is working ok until I close the terminal window.

---

### Post by Vendetta_NZ on 2007-11-07
Have you tried adding the command to the startup programs list? I do it that way and it works fine for me.

---

### Post by SkyCapitan on 2007-11-07
Yes, I tried adding the command to my Autostart folder, but nothing happens with that either.

---

### Post by McButt on 2007-11-15
Try typing the following in the alt+f2 dialog:```
avant-window-navigator &
```
This worked for a friend of mine who had the exact same problem.

---

### Post by SkyCapitan on 2007-11-15
Wow, thanks - that worked perfect!  Good to know I can go back to using my favourite dock  again! :)

---

