---
title: "ATI video drivers, version ?"
date: 2006-02-20
forum: Desktop Environments
---

### Post by rfruth on 2006-02-20
How can I tell what ver my ATI X300 video card is using, is it the 'standard' SVGA driver ? Is there a resource configuration file [http://www-128.ibm.com/developerworks/library/l-config.html#4]("http://www-128.ibm.com/developerworks/library/l-config.html#4") I should look at ?

---

### Post by larsemil on 2006-02-20
fglrxinfo is a nice little program, it should output something like:

```
larsemil@gandalf:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5642 (8.22.5)
```

is that what you are looking for?

---

### Post by rfruth on 2006-02-20
fglrxinfo is a new one for me, thanks !  mine returns ```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
does that mean I am using the generic VGA driver (never have installed ((or been prompted to install)) ATI drivers :confused: 

everything seems to work well, maybe I should leave well enough alone ...

---

### Post by larsemil on 2006-02-20
mesa is the standard if you have not installed anything else. atleast it was for me. 

but there is a really good howto on how to get your aticard running(now u ask me why you would want that as everything is working, i tell u, its going to be a lot faster using 3dgames and stuff)

[ATI CARD HOWTO]("http://ubuntuforums.org/showpost.php?p=423584")

Good luck!

---

