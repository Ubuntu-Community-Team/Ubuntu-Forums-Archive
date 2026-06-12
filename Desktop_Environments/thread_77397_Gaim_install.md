---
title: "Gaim install"
date: 2005-10-16
forum: Desktop Environments
---

### Post by zrothe on 2005-10-16
I'll start with the history of what im doing.

I am trying to install the gaim-xfire plugin. The way gaim is installed w/ ubuntu I guess, it doesn't have a plugins folder. It was recommended to me to remove it and install from source. So I am installing all the dependencies and am stuck at pango.

I have installed GLib and atk.

Here is the error I get while doing the configure process.

> checking for CAIRO... configure: error: *** Didn't find any of FreeType, X11, or Win32.
*** Must have at least one backend to build Pango.[QUOTE][/QUOTE]

---

### Post by zrothe on 2005-10-16
Ok, I found the Cairo archive in their dependencies... im trying to install that but it complains there are no back ends. So then I try installing freetype 2 but it shows under Sympatic package manager that it is installed. I reinstall and still cario complains.

---

### Post by zrothe on 2005-10-16
Ahhh.... don't do it my way kids, my way is bad.

Do it this way instead:

[http://www.ubuntuforums.org/showthread.php?t=44807&highlight=gaim+plugins](http://www.ubuntuforums.org/showthread.php?t=44807&highlight=gaim+plugins)

;)

---

