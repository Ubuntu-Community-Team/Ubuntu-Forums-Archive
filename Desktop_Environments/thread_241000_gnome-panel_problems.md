---
title: "gnome-panel problems"
date: 2006-08-21
forum: Desktop Environments
---

### Post by lateralchaos on 2006-08-21
the panels are completely frozen. like, when i click on them, nothing happens. when i do killall gnome-panel it doesn't help. when i start a session in gnome-failsafe, it says 
"the panel is already running so it wasnt loaded" or something like that. i also get an error that the power management daemon cant start because the dbus session isnt running.
i tried logging in with a new user, and the panel does work, but sound doesnt work, along with some other things.

---

### Post by lateralchaos on 2006-08-21
upon further investigation:
when i try load gnome-panel from a terminal, i get this:
```
(gnome-panel:5909): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5909): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

(gnome-panel:5909): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 24
```

the panel still loads but is unusable.

---

### Post by mithras86 on 2006-08-21
Just copy your ~/.gnome, ~/.gnome2 and ~/.gconfd (sometimes also the ~/gconf) folders (these folders are hidden in your own home dir) to another location (eg ~/backup/). Then restart your computer, and it'll be fixed automaticly. This is a strange bug a lot users mentioned, but afaik this isn't resolved yet.

---

### Post by lateralchaos on 2006-08-21
ok, i figured out the problem. 
after checking all of the processes that were running, i found one that shouldnt be there. xpenguins was the culprit. for some reason it was still there after i restarted.

---

