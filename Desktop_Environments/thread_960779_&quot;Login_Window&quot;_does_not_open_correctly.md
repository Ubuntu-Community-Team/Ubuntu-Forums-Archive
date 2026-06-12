---
title: "&quot;Login Window&quot; does not open correctly"
date: 2008-10-27
forum: Desktop Environments
---

### Post by uho on 2008-10-27
I recently installed ubuntu on my dell inspiron 1525. I was playing around with it and I modified the theme of the login screen via "Login Window". However, now when I try to open this app (System->Administration->Login Window), I see the application dialog flash and then immediately quit.

---

### Post by warleggon on 2008-10-27
This is something to try at least.Open up a terminal window and try:

gksu /usr/sbin/gdmsetup

See if that will allow you to get into the interface.

---

### Post by uho on 2008-10-27
> gdmsetup[13766]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[13766]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[13766]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


This is what the terminal sends back to me


When I run 'sudo gksu /usr/sbin/gdmsetup':
> 
 GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[13795]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[13795]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[13795]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


---

### Post by uho on 2008-10-30
bump*

---

