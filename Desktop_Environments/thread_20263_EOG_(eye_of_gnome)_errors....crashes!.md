---
title: "EOG (eye of gnome) errors....crashes!"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Trab on 2005-03-15
please help me! Eye of Gnome gives this error when started in terminal and crashes when i try to open anything....i have no clue what i could have done to cause this, please help!

```

tedd@raptor:~ $ clear

tedd@raptor:~ $ eog

(eog:4264): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

** (eog:4264): CRITICAL **: file pango-color.c: line 952 (pango_color_parse): assertion `spec != NULL' failed

(eog:4264): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

```
i already tried uninstalling and reinstalling it.... where are these files, "gstrfuncs.c" etc.... i tried "locate" but couldnt find em...
thanks
-Trab

---

### Post by Miguel on 2005-03-16
For locate:

First you must a locate database. Only root can do this, not normal users. To create a locate database, you must issue the command

sudo locate -u

It won't hurt to run it every once in a while to refresh the database (i.e. when installing or uninstalling programs). After that, locate should work.

About eog:

I've found some GTk2 themes crash eog when loading a pic. It also happens when I use those themes under XFce. Try changing the theme to another one (like human, ubuntu's default). The themes that I've experienced to crash eog are:
- gnursid
- blursid (same as above but blue)
- clearlooks window borders (clearlooks deepsky works ok, though)

Hope it helps,

Miguel

EDIT: Changed GTk+ for GTk2. Silly me. What was I thinking on? Physics?

---

### Post by Trab on 2005-03-18
[QUOTE=Trab]please help me! Eye of Gnome gives this error when started in terminal and crashes when i try to open anything....i have no clue what i could have done to cause this, please help!

```

tedd@raptor:~ $ clear

tedd@raptor:~ $ eog

(eog:4264): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

** (eog:4264): CRITICAL **: file pango-color.c: line 952 (pango_color_parse): assertion `spec != NULL' failed

(eog:4264): GLib-CRITICAL **: file gstrfuncs.c: line 1821 (g_strcasecmp): assertion `s1 != NULL' failed

```
i already tried uninstalling and reinstalling it.... where are these files, "gstrfuncs.c" etc.... i tried "locate" but couldnt find em...
thanks
-Trab[/QUOTE]
 i already know that, but thanks.... anyone kno anything more about the actual EOG error? please?!
*bump :-)*

---

