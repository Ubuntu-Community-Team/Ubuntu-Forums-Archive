---
title: "Can't change login screen"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Blajano on 2008-08-06
Hi guys, i'll make it quick P:
I'm trying to change the login screen theme, but somehow i can't. even though i login and logout, reboot, etc. oh and when i run gksu gdmsetup, from the terminal i get this error

```
:~$ gksu gdmsetup
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_set_string: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_to_data: assertion `key_file != NULL' failed
gdmsetup[6201]: GLib-CRITICAL: g_file_set_contents: assertion `contents != NULL || length == 0' failed
gdmsetup[6201]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

```

help?

---

### Post by bunny_basher on 2008-08-06
Can you change it from >System>Administration>Login Window?

---

### Post by Blajano on 2008-08-06
I can see all the themes there as usual, then if to choose one, and logout, the default human theme is still there.

---

### Post by Blajano on 2008-08-06
Oh nvm folks, it's solved now.
But just in case, **[here's the answer]("http://www.linuxquestions.org/questions/ubuntu-63/sudo-gdmsetup-error-messages-658345/")**

---

