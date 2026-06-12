---
title: "'gksudo nautilus' error   :O"
date: 2009-01-29
forum: General Help
---

### Post by reydempto on 2009-01-29
when i enter a terminal and run

```
gksudo nautilus
```

i get this error.

```
Initializing nautilus-share extension
seahorse nautilus module initialized

(nautilus:6222): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6222): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:6222): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:6222): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```


anyone know what this means or how i can fix it?

---

### Post by mc4man on 2009-01-29
Check and see if you have blank cd or dvd media in a drive, if so remove.

---

### Post by reydempto on 2009-01-29
woah dude, i do! that totally worked! thanks a lot

---

### Post by mc4man on 2009-01-29
If you're running Hardy then I don't believe it's been fixed, for Intrepid some recent update fixed (and you can leave/forget that  blank media is inserted

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process.

Another odd fix is to remove any cdroms from your drives as mentioned.

Or try running *gksudo dbus-launch nautilus*.

---

