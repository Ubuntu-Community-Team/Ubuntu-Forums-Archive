---
title: "How can I eep the startbar on top of all windows"
date: 2006-11-23
forum: Desktop Environments
---

### Post by pastorjay on 2006-11-23
I am trying to figure out how to keep the gsdesklet startbar on top of all windows.  Can anyone help me with that?

Thanks!
PJ

---

### Post by not_cool on 2006-11-24
```
$sudo nano -w sudo nano -w /usr/share/gdesklets/Displays/starterbar-desklet/starterbar.display

```

Change```
window-flags="below,sticky"
```
to```
window-flags="sticky"
```

---

### Post by pastorjay on 2006-11-24
Thanks!  Next problem has to do with the color... how can I make that background transparent?  Thanks for all you help!  Look at my screen shot:

[IMG]http://i4.photobucket.com/albums/y150/pastorjay/Computer/Screenshot.png[/IMG]

---

### Post by not_cool on 2006-11-24
I have been trying to figure out why that is until gdesklets began acting weirdly. When I open it it will open its window and put the icon in the gnome taskbar, but the window closes after a second. If I right click on the taskbar icon and select manage desklets, it does the same thing. :( I'll try to fix that soon. I also get this log message:```
Log messages of /home/markus/.gdesklets/logs/gdesklets%3A0.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()
/usr/lib/gdesklets/gdesklets-daemon:119: GtkDeprecationWarning: gtk.threads_enter is deprecated, use gtk.gdk.threads_enter instead
  gtk.threads_enter()
```

---

### Post by not_cool on 2006-11-25
I got gdesklets working but can't figure out how to make that transparent, sorry, hopefully someone else has the answer. Maybe try posting on gdesklets forum.

---

