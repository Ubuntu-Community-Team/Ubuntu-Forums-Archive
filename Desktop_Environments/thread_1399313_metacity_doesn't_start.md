---
title: "metacity doesn't start"
date: 2010-02-05
forum: Desktop Environments
---

### Post by jrockpunk1 on 2010-02-05
So, I recently uninstalled compiz and ccsm on my notebook. However, it also decided to uninstall my window manager for some reason. What happens, is all my window borders are gone so I can't close windows, and lots of other annoyances like that. I can start metacity by going into the terminal and typing:
```

sudo metacity --replace

```
And everything is back to normal. How can I get it to start as a default?

Oh yeah, and when I pressed alt+F2 to open the run-prompt my system went really laggy and then crashed :/

---

### Post by drs305 on 2010-02-05
With metacity already installed, this should do it:

System, Preferences, Appearance: Visual Effects >> None.

---

### Post by jrockpunk1 on 2010-02-05
It's already on "none". Also, there's still problems when I do "sudo metacity --replace &". For instance, I closed the terminal and at the bottom of the screen it still showed the terminal as if minimized, and nothing happened when I clicked it.

Do I need to reinstall my window-manager?

[edit]
After enabling metacity, it reverted and when I opened a terminal it crashed.

---

### Post by lidex on 2010-02-05
Try this in your gconf editor. "Applications>System Tools>Configuration Editor". Drill down to "Apps>Metacity>General". In the right pane put a tick in the box for "compositing_Manager". Logout/in.

---

### Post by jrockpunk1 on 2010-02-05
Did it, ticked the box and it still doesn't work.

---

### Post by yester64 on 2010-02-05
I have a similar problem.
Metacity is enabled once you run 'metacity --replace'.

But i have the same problem that my windows bars are gone if i disable the effects.

> There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 

(gnome-appearance-properties:2637): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

(gnome-appearance-properties:2638): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

This is what is in my xsession-error log.
I installed some themes and removed some. But i would like to have the default back and have effect disabled.

Perhaps that will solve both of our problems.
Is _**[COLOR=black]ubuntulooks[/COLOR]**_ standard? Or is there a way to see what is by default installed?

---

### Post by jrockpunk1 on 2010-02-05
Even with metacity enabled I get problems. I don't think it's a problem with metacity. Anybody think how I can fix this? Is there any way to reinstall the whole desktop manager?

---

### Post by lidex on 2010-02-05
Metacity is the window manager, gtk-window-decorator is the window decorator. Problems with window borders fall into the decorator area. Try going to "Applications>System>Preferences>Startup Applications". Click "Add" and in the command field enter:
```
gtk-window-decorator
```
Put something descriptive in the name field;comments optional.
Click "Add" then "Close" then reboot

---

### Post by lidex on 2010-02-05
Metacity is the default window manager for ubuntu. If you uninstall compiz it should revert. If metacity is running and you try to start it from a terminal you will have problems. Missing window borders can be fixed by running this command in an Alt+F2 run dialog:
```
gtk-window-decorator --replace
```
See above post to make persistent or once everything is correct, in startup applications 2nd tab place a tick in box to "automatically remember running applications when logging out"

---

### Post by jrockpunk1 on 2010-02-05
Sorry mate, you were JUST too late. I've reinstalled ubuntu now :P

No matter, only took 5 minutes and as I didn't have anything on there (only installed it earlier today) it didn't matter.

However, I'll come back to this page and look at those suggestions should the problem arise again.

---

