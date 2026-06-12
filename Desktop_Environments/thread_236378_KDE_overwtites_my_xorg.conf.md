---
title: "KDE overwtites my xorg.conf"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Mandor on 2006-08-14
I have the following problem: since the automatic xorg.conf configuration is far from perfect, I manually configured mine, but it seems that KDE is overwriting it thus spoiling some of the configurations I make.

Is there any way to prevent that (other than not using KDE :) ).

---

### Post by SoggyCornflake on 2006-08-14
You might try removing write permissions for the xorg.conf file

from a terminal in the directory wherever xorg.conf exists type:

[INDENT]**chmod 444 xorg.conf**
[/INDENT]
That ought to prevent kde from overwriting it.  However, I'm not sure it doing that could cause other problems.

---

### Post by ardchoille on 2006-08-14
Keep in mind that root still has the power to delete a -r--r--r-- file.

---

