---
title: "ATI driver not running correctly"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Alpha_Cluster on 2006-06-03
I installed fglrx and did the xorg reconfigure. It still give me this message though:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

Im runing a laptop with a AMD 64 3000+
and the graphics card is a Radeon 9700 PRO

---

### Post by VFiend on 2006-06-03
[QUOTE=Alpha_Cluster]I installed fglrx and did the xorg reconfigure. It still give me this message though:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

Im runing a laptop with a AMD 64 3000+
and the graphics card is a Radeon 9700 PRO[/QUOTE]
Add the line ```
load "dri"
``` to Section "Module"' in xorg.conf.

EDIT: I just added this to the wiki page because I had the problem and other people seem to be having it too.

---

### Post by Alpha_Cluster on 2006-06-03
ok now i bet your guna call me crazy but i for some reason cant open that file...

i typed:  sudo gedit /etc/x11/xorg.conf
but it only brings up an empty gedit window.

---

### Post by VFiend on 2006-06-03
I think it's /etc/X11/xorg.conf (the capital X is needed!)

---

### Post by Alpha_Cluster on 2006-06-03
Ok im in it now but its already writen in the xorg.conf

Could haveing Xgl installed be causing this?

---

### Post by VFiend on 2006-06-03
Maybe, I don't know much about Xgl at all. Hopefully someone else can help.

---

