---
title: "AWN Dock and Rhythmbox 'error'"
date: 2011-01-10
forum: Desktop Environments
---

### Post by Soldier2580 on 2011-01-10
Ok, I've just finished installing the AWN dock, and all went well, until rhythmbox (just playing in the background) switched to the next song. 
A sort of error-popup window pops open to let me know what the next song is called. (see screenshot)
I've searched for similar problems, and i think it has something to do with a notification applet of AWN conflicting with the one in my panel, the only problem is, there is none active.. 
I've tried restarting AWN when I quit the gnome notification area, but that didn't help.


This is VERY annoying, since I have music playing constantly, and so I keep getting these little windows trown at my face! Any help is very, very much appreciated :)

S2580

---

### Post by Soldier2580 on 2011-01-10
This is what i get for running it via the terminal, if it helps..

> soldier@soldier-laptop:~$ avant-window-navigator 
Screen is composited
** (avant-window-navigator:24500): DEBUG: Updating gtk theme colours
** (avant-window-navigator:24500): DEBUG: Updating dialog colours
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24502] for "awnterm.desktop", UID: 1294695754, XID: 23068719
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24504] for "taskmanager.desktop", UID: 1294698588, XID: 23068720
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24505] for "file-browser-launcher.desktop", UID: 1294696246, XID: 23068721
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24506] for "mail.desktop", UID: 1294696564, XID: 23068722
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24507] for "garbage.desktop", UID: 1294695590, XID: 23068723
** (avant-window-navigator:24500): DEBUG: Spawned awn-applet[24508] for "weather.desktop", UID: 1294695889, XID: 23068724

(awn-applet:24502): GLib-GObject-WARNING **: g_object_newv: construct property "panel-id" for object `AwnTerminalApplet' can't be set twice
** (awn-applet:24502): DEBUG: awn-terminal.vala:80: keybinding: 
** (awn-applet:24502): DEBUG: awn-terminal.vala:80: keybinding: 
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
/usr/lib/pymodules/python2.6/awn/extras/awnlib.py:414: GtkWarning: IA__gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed
  self.__parent.set_tooltip_text(text)
/usr/lib/pymodules/python2.6/awn/extras/awnlib.py:414: GtkWarning: IA__gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed
  self.__parent.set_tooltip_text(text)



---

### Post by moonbeam on 2011-01-10
It's not related to awn-notification-daemon / notify-osd, which appears to be what you're referring to above.

From the screenshot it appears that rhythmbox itself is opening those windows,  I assume this issue persisted after a restart of rhythmbox?

---

### Post by Soldier2580 on 2011-01-11
Yeah, I thought it was AWN, since I was messing around with the applets when it started. A restart of rhythmbox didn't work, and a reboot didn't either. 
Somehow, when I started to play some music now, nothing abnormal happened.. I don't know what started this, and now I don't know what ended it.. I'm just kinda glad :) All i did was hibernate my pc for the night.
Well, thanks anyway :) I'm sorry I can't give a proper solution for this, but I'll mark it as solved anyway.

---

