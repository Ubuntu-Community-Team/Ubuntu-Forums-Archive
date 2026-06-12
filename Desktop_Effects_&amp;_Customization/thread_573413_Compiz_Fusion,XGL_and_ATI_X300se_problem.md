---
title: "Compiz Fusion,XGL and ATI X300se problem"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by ludovic23 on 2007-10-11
Hello ppl,

Am new to this forum i just install ubuntu and its a great OS i love it.
i have a little problem i install Compiz fusion and XGL on my PC using ATI X300SE
Its working but my direct rendering: No

when i type  glxinfo | grep rendering i got this error anybody can help me on this?
 
[B]Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No[/B]

---

### Post by swisscow on 2007-10-12
This can be a right pain in the rear to sort out. Personally I am waiting for the new 8.42 drivers from ATI which supposedly support compiz without XGL - i.e. straight out of the box.

They are due in the next few days (supposedly again). If they do turn up and they work expect lots of comments on the forums!

---

### Post by Forlong on 2007-10-12
ludovic23, please log into your regular session (not Xgl) and run
```
fglrxinfo
```

---

### Post by ludovic23 on 2007-10-12
i got this when i type fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6747 (8.40.4)

---

### Post by Forlong on 2007-10-12
And what gives ```
glxinfo | grep "direct rendering"
``` now (in your regular session)?

---

### Post by rjbgbo on 2007-11-04
My tests

rjbgbo@rjbgbo-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X300/X550/X1050 Series
OpenGL version string: 2.0.6473 (8.37.6)


rjbgbo@rjbgbo-desktop:~$ glxinfo | grep "direct rendering"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

My problem - [http://ubuntuforums.org/showthread.php?p=3703291&posted=1#post3703291](http://ubuntuforums.org/showthread.php?p=3703291&posted=1#post3703291)

---

