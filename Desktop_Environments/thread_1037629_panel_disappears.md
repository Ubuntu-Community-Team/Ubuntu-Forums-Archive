---
title: "panel disappears"
date: 2009-01-12
forum: Desktop Environments
---

### Post by cprophecy on 2009-01-12
I'm running 8.04. this has happened several times on several different installations. I'm not sure how i can fix it other than rebooting. I've googled and found threads but nothing conclusive. Of course rebooting to fix a gui problem is unacceptable so if anyone knows what i can do please let me know, thank you.

when I run gnome-panel:

```
gnome-panel

(gnome-panel:14921): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(gnome-panel:14921): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(gnome-panel:14921): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(gnome-panel:14921): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: 
runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
```

---

### Post by blueshiftoverwatch on 2009-01-12
Entering "**sudo metacity --replace**" into the terminal should reload the entire Metacity window manager which might fix your panel problems. At least for the the current session anyway.

Hopefully that will have helped until someone more knowledgeable comes along and sees this thread.

---

### Post by gettinoriginal on 2009-01-12
I am not much more knowledgeable than others, but the next time, before you log in, go to options, sessions, and choose gnome, change session.  Hopefully this will help  :p

---

### Post by cprophecy on 2009-01-12
> **blueshiftoverwatch said:**
> Entering "**sudo metacity --replace**" into the terminal should reload the entire Metacity window manager which might fix your panel problems. At least for the the current session anyway.

Hopefully that will have helped until someone more knowledgeable comes along and sees this thread.

this removed the title bars from my windows, and now i cant type into terminals or select windows with the mouse. it gave error messages but i cannot copy them to a file now. now nothing works..

---

### Post by gettinoriginal on 2009-01-12
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

---

### Post by blueshiftoverwatch on 2009-01-12
> **cprophecy said:**
> this removed the title bars from my windows, and now i cant type into terminals or select windows with the mouse. it gave error messages but i cannot copy them to a file now. now nothing works..
Sorry about that. Those changes should go away after logging back in or restarting the computer.

---

