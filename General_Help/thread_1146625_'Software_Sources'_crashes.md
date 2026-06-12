---
title: "'Software Sources' crashes"
date: 2009-05-02
forum: General Help
---

### Post by Bungo Pony on 2009-05-02
Running Hardy. Whenever I open 'Software Sources' and I try to import a key file under 'Authentication', it crashes. I ran it from a terminal and this is what I got:

```

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(software-properties-gtk:13248): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
sys:1: Warning: g_error_free: assertion `error != NULL' failed

(software-properties-gtk:13248): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(software-properties-gtk:13248): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

```

Either I need to fix what's causing it to crash, or I need to import the key manually (but where?)

---

### Post by Bungo Pony on 2009-05-02
Found the way to do it manually:  sudo apt-key add /home/..../keyfile

Still don't know why the bloody thing crashes :confused:

---

