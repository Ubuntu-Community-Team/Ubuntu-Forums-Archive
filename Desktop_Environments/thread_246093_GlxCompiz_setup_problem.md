---
title: "Glx/Compiz setup problem"
date: 2006-08-28
forum: Desktop Environments
---

### Post by waldick on 2006-08-28
I tried to set up Glx/Compiz via the tutorial at "ubuntuguide.org" for nvidia...i egt part of the way through and when i try to:

gksudo gedit /etc/gdm/gdm.conf-custom ...

i get this:


X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gedit:11419): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:11419): WARNING **: Could not load python module modelines


** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

** (gedit:11419): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGI N (plugin)' failed

i have followed the tutorial by cutting and pasting, so i don't think i made any typo's...anyhow, when i try to start compiz by the "thefuture", i get this:

"gnome-window-decorator, Failed to load shadow images
compiz.real: No composite extension"

i suspect its a simple fix, but it is apparently beyond me....

of course, i am fairly new to this...

looks to me like i'm missing some sort of plug-in, but i've searched for one with a name remotely like the error message, but no luck...


j

---

### Post by waldick on 2006-08-29
anyone....

---

### Post by waldick on 2006-08-29
ok, got it working through the trial and error method...windows are wavy and i can spin the desktop cube, but only with the mouse...i cannot get it to work with the keystrokes...also, it wont let show smaller versions of all the open windows ala osx...am i missing a package, or is it in some config file ?

j

---

