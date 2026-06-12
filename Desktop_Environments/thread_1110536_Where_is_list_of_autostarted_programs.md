---
title: "Where is list of autostarted programs?"
date: 2009-03-29
forum: Desktop Environments
---

### Post by jmjohn on 2009-03-29
Hey all,

I want to manage xfce's list of autostart applications and remove some of them.  Does anyone know where the configuration file with this list of programs is?

Thanks!
-glass.dimly

---

### Post by Name141 on 2009-03-29
Applications -> Settings - Settings Manager -> AutoStarted Apps ?

---

### Post by kerry_s on 2009-03-29
in the menu look for autostart programs, from there you can add/delete/stop programs

---

### Post by sisco311 on 2009-03-29
The .desktop files are in ~/.config/autostart/.

a typical .desktop file looks like this:
> 
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=*name*
Comment=*comment*
Exec=*/path/to/executable*
StartupNotify=false
Terminal=false
Hidden=false


If you don't want to run the app at login, change *Hidden=false* to *Hidden=true*.

But the GUI provides a nice interface to manage the apps.
In Xfce 4.6 go to Menu -> Settings -> Xfce4 Settings Manager -> Session and Startup, Application Autostart tab.

---

