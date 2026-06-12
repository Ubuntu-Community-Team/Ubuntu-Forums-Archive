---
title: "Making Metacity lie down. (Karmic)"
date: 2009-12-04
forum: Desktop Environments
---

### Post by brilyant on 2009-12-04
Being one who likes to hunt with the hounds and run with the hare, I like using fvwm as the WM on a Gnome desktop.

I have read the [SOLVED] thread about Metacity bouncing back up like a naughty puppy. This seems now to require considerable editing of config files.

 With previous versions of Gnome I think it was possible to prevent Metacity restarting using the Current Session tab of gnome-session-properties.  This allowed you to switch Metacity from "Restart" to "Normal".

This tab is no longer offered. Does anyone know exactly how it used to effect this switch?

---

### Post by ajgreeny on 2009-12-04
I don't know fvwm at all, but you could try using the command ```
fvwm --replace
``` in the System->Preferences->Startup Applications utility window.  This assumes that the command *fvwm --replace* will give you that WM in the first place, which is the part of this answer that I know nothing about.

---

