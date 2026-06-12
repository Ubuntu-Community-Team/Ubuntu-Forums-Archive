---
title: "Cairo dock dbus methods?"
date: 2009-01-23
forum: Desktop Environments
---

### Post by mbeierl on 2009-01-23
Does anyone know where I can find info on how to change the cairo dock position via Dbus?  When I activate my second monitor the dock goes off the bottom of the screen, and I'd like to programmatically change its location.

---

### Post by fabounet on 2009-01-23
the DBus plug-in gives you some methods.
as I didn't receive a lot of wishes, it is quite limited.
there is a method that allow you to reload your dock's config, maybe that would be enough in your case.
Cairo-Dock2 has the Xinerama support by the way, which may suit you better.

---

### Post by mbeierl on 2009-01-23
Thanks!

Where does one find Dock 2?

---

### Post by mbeierl on 2009-01-23
Ah... followed this
[http://ubuntuforums.org/showthread.php?p=6557080](http://ubuntuforums.org/showthread.php?p=6557080)
to 
[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

but... now that I have them installed, I realize, I'm on AMD64.

What sort of environment does one need to compile from source (or does someone have a 64 bit deb somewhere?)

---

### Post by mbeierl on 2009-01-23
Ok, I followed the directions that I managed to locate here:

[http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20SVN&lang=en)

and was able to get it to compile.  The tarballs seemed to be missing some files.

The xinerama support is great, with the only exception of auto hiding the dock on the bottom of a screen that is shorter than the secondary does not seem to work :)

Thanks very much! (And Cairo Dock 2 is looking excellent!)

---

