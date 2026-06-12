---
title: "Compiz Fusion Error"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by shawnlogic on 2007-09-15
Hi Everyone,

I just installed compiz fusion according to this guide: [http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

when i type compiz --replace in the terminal, i get the following errors:

```
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Everything in the install went well, i'm using ubuntu 7.04 with intel integrated graphics.
But nothing is working.  None of the Effects.

Does anyone know a possible fix?

Thanks in advance.


EDIT: I solved this problem by uninstalling all compiz packages and followed this guide: [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
and it worked!!!

---

