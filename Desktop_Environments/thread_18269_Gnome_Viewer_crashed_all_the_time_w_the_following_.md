---
title: "Gnome Viewer crashed all the time w/ the following errors:"
date: 2005-03-05
forum: Desktop Environments
---

### Post by yoha on 2005-03-05
(eog:5613): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

** (eog:5613): CRITICAL **: file pango-color.c: line 952 (pango_color_parse): assertion `spec != NULL' failed

(eog:5613): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

    These are the errors i got when i issue $eog /path/to/picture/file. Double clicking on a graphic file of any kind /*.png, .jpg, etc*/ will crash eog. I have tried reinstalling the program via apt-get but eog still crashes on me. Anyone has come across these errors before?

-y0ha

---

### Post by jerome bettis on 2005-03-05
you're using some sort of desktop theme right?

eog doesn't support them yet.

ditch your theme or use a different image viewer.  search this forum for eye of gnome, there's a few threads on it, including some recommendations for better programs.

---

### Post by yoha on 2005-03-05
[QUOTE=jerome bettis]you're using some sort of desktop theme right?

eog doesn't support them yet.

ditch your theme or use a different image viewer.  search this forum for eye of gnome, there's a few threads on it, including some recommendations for better programs.[/QUOTE]

jerome, thanks! it was indeed incompatible w/ the Clearlooks engine.

---

