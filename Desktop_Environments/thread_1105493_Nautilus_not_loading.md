---
title: "Nautilus not loading"
date: 2009-03-24
forum: Desktop Environments
---

### Post by Geffers on 2009-03-24
I'm using v8.04 (hardy heron) which has been operating without an obvious problem  for many months.

I have launched Nautilus from sudo in the past but now am getting the following error message;

geoff@Columbia:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension

(nautilus:10010): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10010): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:10010): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10010): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault
geoff@Columbia:~$ 

I have tried to reinstall Nautilus via synaptic but this did not resolve the matter.

Any hints appreciated.

Geffers

Apologies folks, didn't see the thread outlining the problem before I posted.

---

