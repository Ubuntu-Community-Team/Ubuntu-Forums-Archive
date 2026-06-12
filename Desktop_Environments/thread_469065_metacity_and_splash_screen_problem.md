---
title: "metacity and splash screen problem"
date: 2007-06-09
forum: Desktop Environments
---

### Post by Morbett on 2007-06-09
I installed some common Ubuntu Studio packages just now, and now when I boot up I have two problems:

1) The GNOME splash screen hangs a bit after Nautilus boots up, so I still see it on the desktop for 20 seconds or so after everything is fully booted.

2) I have no title bar (metacity) at all.

Any ideas?

---

### Post by Morbett on 2007-06-09
Just to clarify, when I say the splash screen is hanging, in fact it's more like it comes back for a few seconds if I try to click on something.  For example, I go to open a folder on my desktop and the splash screen pops up for a bit and there is no metacity title bar too.

Strange...

---

### Post by cor2y on 2007-07-07
you can try this

Launch the gconf editor.
In the terminal its
> gconf-editor

You are going to desktop->gnome-applications->window_manager
change the **default setting**, **not** the current setting, from /usr/bin/whatever
to /usr/bin/metacity 
Then restart x metacity should now boot with no hanging.

if metacity is there it could be a startup script in your session

---

