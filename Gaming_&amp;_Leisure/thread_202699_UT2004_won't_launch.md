---
title: "UT2004 won't launch"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by YourDoom123 on 2006-06-23
```

arjun@arjun-laptop:~$ ut2004
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History:

Exiting due to error


```

/cry

yes, i'm currently testing edgy, but this is on a dapper install. my fglrxinfo displays the correct info, so i know my drivers are installed. the only info i could find was that i had mesa libs lying around, but i'm running xgl/compiz, which require the mesa libs... is this an incompatibility? does anyone know of a fix?

---

### Post by YourDoom123 on 2006-06-24
FIXED!

just had to use the nonXGL script: [http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

---

