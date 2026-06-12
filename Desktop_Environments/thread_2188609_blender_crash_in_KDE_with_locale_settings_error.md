---
title: "blender crash in KDE with locale settings error"
date: 2013-11-18
forum: Desktop Environments
---

### Post by Bartje on 2013-11-18
Hi all,

when running Blender in KDE, it crashes when rendering with cycles and having textures. I'm fairly sure it's a KDE-settings problem, because it happens in KDE not in XFCE.

The error I get is :  locale::facet::_S_create_c_locale name not valid

So I tried changing locale settings from the settings menu in KDE, but so far, no luck.

Annyone with a similar issue having solved this?

Thanks.

Bart

---

### Post by Bartje on 2013-11-18
OK,

found the issue myself already :-)

in setlocale.sh I changed :

export LANG=nl_BE.ISO-8859-1
to
export LANG=nl_BE.UTF-8

question:
why ISO-8859-1 ? I've read on the blender website it is less and less used, mostly UTF-8

---

### Post by Bartje on 2013-11-21
I now discovered that this also fixed amarok, it now loads my music collection again :-D

---

