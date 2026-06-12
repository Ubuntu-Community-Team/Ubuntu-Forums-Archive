---
title: "[SOLVED] can't &amp;quot;sudo nautilus&amp;quot; on fresh Hardy install"
date: 2009-01-01
forum: Desktop Environments
---

### Post by Sin@Sin-Sacrifice on 2009-01-01
Just sort of solved... I personally think we should be able to open a root nautilus window with a blank DVD in the drive. But taking it out works.

Anybody recognize this? I seen a few similar nautilus error codes on google but nothing regarding sudo. I can get a non-root nautilus just fine. Although when I type nautilus into the terminal I get the second code as follows:

1st: ```
Killmandline:+$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-image-converter extension
Initializing nautilus-share extension

(nautilus:23196): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:23196): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:23196): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:23196): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```


2nd ("normal" nautilus): ```
Killmandline:+$ nautilus

(nautilus:23204): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
```

---

### Post by my_key on 2009-01-01
Does "gksu nautilus" or "gksudo nautilus" work?

---

### Post by Sin@Sin-Sacrifice on 2009-01-01
I get the password verification box with gksudo but this error report: ```
Killmandline:+$ gksudo nautilus

(gksudo:23417): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Initializing nautilus-image-converter extension
Initializing nautilus-share extension

(nautilus:23418): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:23418): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:23418): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:23418): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
``` with both.

---

### Post by Sin@Sin-Sacrifice on 2009-01-01
Oh weird... with a little cut and paste and some reforming of sentence structure I found this [https://bugzilla.redhat.com/show_bug.cgi?ctype=xml&id=458586](https://bugzilla.redhat.com/show_bug.cgi?ctype=xml&id=458586) bug in google and wouldn't you know that I did have a blank DVD-R in the drive. Seems to be a bug in nautilus and how it handles blank's folders. That's just strange to me. sudo nautilus works now without the dvd in the drive. Thanks looking into it My_Key (Mikey?)

---

### Post by my_key on 2009-01-01
That's a weird bug. Glad it worked out. 

Cheers,
Michael

---

