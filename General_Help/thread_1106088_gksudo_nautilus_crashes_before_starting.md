---
title: "gksudo nautilus crashes before starting"
date: 2009-03-25
forum: General Help
---

### Post by prylux on 2009-03-25
I typed the command gksudo nautilus in the terminal and I got this:
[INDENT]
(nautilus:13595): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing nautilus-share extension
seahorse nautilus module initialized

(nautilus:13595): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:13595): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(nautilus:13595): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(nautilus:13595): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)[/INDENT]


It was working before the last update.

---

### Post by albandy on 2009-03-25
try with the path
gksudo nautilus /
or sudo nautilus /

---

### Post by prylux on 2009-03-25
> **albandy said:**
> try with the path
gksudo nautilus /
or sudo nautilus /

Nothing happened at all...

---

### Post by KCG102282 on 2009-03-25
Try gksu

---

### Post by prylux on 2009-03-25
> **KCG102282 said:**
> Try gksu

I just tried that and got the same warnings

I also tried "gksu "nautilus --no-desktop"

with the same results as in the first post

---

### Post by prylux on 2009-03-25
Fixed the issue and here is how...

Rebooted and at GRUB selected "recovery mode"
Gave root password
At prompt typed in "startx"
Clicked OK when warned about being logged in as root
Opened up nautilus (worked)
Just to be sure I opened a terminal and typed in gksudo nautilus (worked)
Logged out and rebooted

Started up normally and gksudo nautilus worked.

I don't know what the problem was or why this fixed it.

Thanks for the help...:)

---

