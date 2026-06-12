---
title: "problem occored during update"
date: 2005-04-06
forum: Desktop Environments
---

### Post by bw32 on 2005-04-06
E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0

does anyone have any idea on how we may go solve it?

thanks

---

### Post by zAo on 2005-04-07
The file is used by both packages. You must force apt to overwrite. Be warned: your direct rendering will be gone! 

Use `man apt-get` to see for the overwrite (no-dept) command.

---

### Post by bobmitch on 2005-04-07
[QUOTE=bw32]E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-10_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0

does anyone have any idea on how we may go solve it?

thanks[/QUOTE]

See [this](http://www.ubuntuforums.org/showthread.php?t=22984&highlight=mesa) thread.

Basically, you will have to remove the fglrx package (which you manually installed after converting to a .deb from an .rpm I assume) - try updating again, this should work - then reinstall the fglrx deb.

No reconfiguration should be necessary - details are in the thread I linked to.  If you have problems, PM me or reply here.

---

