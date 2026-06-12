---
title: "DontZap option isn't enough to disable Ctrl Alt Backspace"
date: 2006-09-03
forum: Desktop Environments
---

### Post by karvus on 2006-09-03
I've added the 

```

Section "ServerFlags"
        Option          "DontZap"               "yes"
EndSection

```

To my /etc/X11/xorg.conf file, and from /var/log/Xorg.93.log says that the server recognized it:

```
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "DontZap" "yes"
(II) Module ABI versions:

```

But Ctrl-Alt-Backspace still zaps my server.  I'm guessing the window manager is eating it.  I'm using the compiz and gnome-windows-decorator.

Any ideas how I disable it?  And if I could get GTK+ from eating my F8 at the same time it would be great.


Thomas

---

### Post by karvus on 2006-09-05
No clues available? :)

---

