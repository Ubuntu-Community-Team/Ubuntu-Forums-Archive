---
title: "XGL and compiz with UT2004"
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by waltervalderrama on 2006-08-15
It's been a while since i installed xgl and compiz on my P4 2.0 GHz, 512 RAM and Gforce MX 440. Before I played UT2004 and alien arena 2006 perfectly. But now every 3D game displays on a portion of the screen. If I want to have full screen I have to set 1152 x 864 but performance decreases dramatically.

How can I have a normal full screen as before???????????

---

### Post by TripleE on 2006-08-15
check out this post:
[http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

---

### Post by Garfield360 on 2006-08-15
Can you now play games on linux such as football manager, battlfield 2 etc as I allways thought linux you couldnt get the games to work?

---

### Post by alx77 on 2010-06-01
in your ut2004.sh wrap lines:

unset LIBGL_ALWAYS_INDIRECT
exec "./ut2004-bin" $*
LIBGL_ALWAYS_INDIRECT=1

Compiz'z no problem now!
I very like this game even now (almost like ubuntu), enjoy guys!:guitar:

---

