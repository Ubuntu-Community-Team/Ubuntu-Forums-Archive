---
title: "Segfault"
date: 2009-03-22
forum: General Help
---

### Post by linuxisevolution on 2009-03-22
I keep getting segmentation faults with reconstructor:

```


(reconstructor.py:24466): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
/usr/bin/reconstructor: line 4: 24466 Segmentation fault      sudo python reconstructor.py

```

Anyone know of a fix?

---

