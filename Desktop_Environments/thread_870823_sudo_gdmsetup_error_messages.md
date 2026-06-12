---
title: "sudo gdmsetup error messages"
date: 2008-07-26
forum: Desktop Environments
---

### Post by r11_kaede on 2008-07-26
Hi all,

I'm new to Ubuntu, so pardon me if I ask any questions that may sound pretty dumb. :D

Anyway, I've been trying to edit my login preferences via the login window, but it wouldnt let me save cos I wasnt in root.

So I went "sudo gdmsetup".

But it gives me lots of error messages, as stated below.

----

gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[9737]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[9737]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

------

If anyone could help me interpret these messages, I would be very grateful.

Thanks :D

---

### Post by babounours on 2008-07-26
are you ingraphical mode then?

---

### Post by r11_kaede on 2008-07-26
it allowed me to go into graphical mode for login window, but no changes can be saved. even if i select the changes, then press close, the original settings pop back again.

and yes, i'm currently in graphical mode for all, if thats what you are asking :)

---

### Post by upchucky on 2008-07-26
cant have gdm running when trying to do stuff to it that changes how it runs. running a desktop terminal is not the same as pure CLI. you must stop the GDM first.

it must be tweaked from the command line, after backing up. make sure sys is updated first.

---

### Post by r11_kaede on 2008-07-27
hi, could you kindly tell me how to tweak it then? :)

---

### Post by Zaiken on 2009-08-17
I'm havin this same problem. Anyone figure out how to fix?

---

