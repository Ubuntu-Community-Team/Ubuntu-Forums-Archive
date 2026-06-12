---
title: "sudo nautilus error"
date: 2009-04-27
forum: General Help
---

### Post by yim on 2009-04-27
for awhile now I've been able to give the terminal command and move files around without any trouble but as of the last couple of updates I get the following error using 8.04

sudo nautilus

Initializing nautilus-share extension
Initializing nautilus-open-terminal extension
seahorse nautilus module initialized

(nautilus:7236): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7236): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:7236): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7236): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)
Segmentation fault



does anyone know what's happened? any help appreciated

thanks yim

---

### Post by danwood76 on 2009-04-27
You could try running gksudo instead of sudo.
They work differently and get permissions differently so its worth a shot.

If one of nautilus' settings files is corrup you could try delelting the nautilus settings folder from the root user:
```

sudo rm -R /root/.nautilus

```
Be careful when you type this into the terminal, just copy and paste to be safe, as if you type it wrong you could delete the wrong folder and bork your system!

---

### Post by _Purple_ on 2009-04-27
It is better to use gksudo instead of sudo when opening a graphical applications.

```
gksudo nautilus 
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mcduck on 2009-04-27
Do you get the same errors if you use "gksudo nautilus"?

"sudo" shouldn't really be used for any graphical applications, it doesn't load root's environment correctly for graphical applications which can in some cases have quite nasty results (like overwriting stuff in your home directory with root permissions, making you unable to change the settings or even log in at all).

As a rule, use "sudo" for CLI tasks, and "gksudo" for graphical tasks.

---

### Post by yim on 2009-04-27
tried gksudo nautilus
and this is what happens


Initializing nautilus-share extension
Initializing nautilus-open-terminal extension

(nautilus:7301): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7301): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(nautilus:7301): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:7301): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


have to go to work right now will try others this evening

thanks for the suggestions guys

yim

---

