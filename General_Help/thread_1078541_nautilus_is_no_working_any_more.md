---
title: "nautilus is no working any more ????"
date: 2009-02-23
forum: General Help
---

### Post by anayisse on 2009-02-23
Hi every body ..

sudo Nautilus is no working any more I'm getting those errors :

~$ sudo nautilus

seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:10263): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10263): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:10263): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10263): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault


~$ gksudo nautilus
seahorse nautilus module initializedInitializing nautilus-share extension

(nautilus:10297): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10297): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed



can you help me please

---

### Post by EricStJean on 2009-03-03
> **anayisse said:**
> Hi every body ..

sudo Nautilus is no working any more I'm getting those errors :

~$ sudo nautilus

seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:10263): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10263): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:10263): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10263): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault


~$ gksudo nautilus
seahorse nautilus module initializedInitializing nautilus-share extension

(nautilus:10297): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10297): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed



can you help me please



For me (and others..., you could see in forums) this disappear removing a blank CD in the cdrw drive...  ;)

---

### Post by billstei on 2009-04-16
Or even if the CD is not blank.  Nautilus 2.24.1 produces a segmentation fault.

---

