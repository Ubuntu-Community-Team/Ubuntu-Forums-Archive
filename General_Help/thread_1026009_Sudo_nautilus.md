---
title: "Sudo nautilus"
date: 2008-12-30
forum: General Help
---

### Post by Bofur on 2008-12-30
When I try using the command 'sudo nautilus' in terminal I get this ouput:
```
Initializing nautilus-share extension
seahorse nautilus module initialized

(nautilus:10828): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10828): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:10828): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:10828): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault

```

It never did this before. Anyone know whats going on?

---

### Post by oldos2er on 2008-12-30
You should be using "gksu nautilus," since Nautilus is a graphical program (see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)). This may not help in solving your seg fault though.

---

### Post by gjoellee on 2008-12-30
> **oldos2er said:**
> You should be using "gksu nautilus," since Nautilus is a graphical program (see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)). This may not help in solving your seg fault though.

either "gksu"
or maybe you can do:
```
sudo su
```
and then
```
nautilus
```

---

### Post by Bofur on 2008-12-30
Same error with gksu nautilus and su sudo then nautilus.

---

### Post by akelsall on 2008-12-30
I haven't ran into that problem (or any problem) related to Nautilus (in Ubuntu 8.04 or 8.10). Maybe try removing and re-installing nautilus:

```
sudo aptitude remove nautilus

sudo aptitude install nautilus
```

Andy

---

### Post by Yashiro on 2009-02-21
You can sometimes fix this by closing and restarting the bonobo activation process.

Another odd fix is to remove any cdroms from your drives and retry.
Odd indeed, but it works.

Or try gksudo dbus-launch nautilus.

---

