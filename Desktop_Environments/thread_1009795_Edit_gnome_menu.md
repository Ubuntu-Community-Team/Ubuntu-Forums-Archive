---
title: "Edit gnome menu?"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Izek on 2008-12-12
Little off-topic or so, but I'd like to do something similar, but rather than just greying out the recent docs menu, I'd like to have the menu as follows. Things crossed out I want to have removed. I'd also like to change the system menu as well to remove the things I crossed out.

---

### Post by bapoumba on 2008-12-13
Moved to its own thread :)

Edit: have you tried System > Prefs > Main Menu ?

---

### Post by itsbradman on 2008-12-13
This one belongs here.  I no longer have any options in my menu editor for creating new launchers, options, etc.  Also no menu editor in sys pref?!?!
I've attached a screenshot.  Help!!

---

### Post by CholericKoala on 2008-12-13
> **Izek said:**
> Little off-topic or so, but I'd like to do something similar, but rather than just greying out the recent docs menu, I'd like to have the menu as follows. Things crossed out I want to have removed. I'd also like to change the system menu as well to remove the things I crossed out.

in terminal, "gconf-editor"

Go to apps, panel, global.

---

### Post by itsbradman on 2008-12-13
I see nothing in there that will fix the problem I am having.

---

### Post by Izek on 2008-12-13
> **itsbradman said:**
> I see nothing in there, [gconf-editor], that will fix the problem I am having.

Same for my problem, just for the help and support, about gnome and about ubuntu can't be removed from gconf-editor. See attachment first attachment

Also, System > Prefs > Main Menu doesn't have places at all and it doesn't show the other system menu items. See other attachment

---

### Post by CholericKoala on 2008-12-15
> **itsbradman said:**
> I see nothing in there that will fix the problem I am having.

Go to where I said last time.

"disable_log_out"  "disable_lock_screen"

experiment a little

It did it for me just fine.

---

