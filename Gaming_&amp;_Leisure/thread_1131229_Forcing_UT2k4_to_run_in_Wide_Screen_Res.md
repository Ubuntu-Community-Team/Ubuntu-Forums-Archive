---
title: "Forcing UT2k4 to run in Wide Screen Res?"
date: 2009-04-20
forum: Gaming &amp; Leisure
---

### Post by beastrace91 on 2009-04-20
Is there a way I can force UT2k4 to run in a wide screen resolution? It makes me sad having black bars on either side of my 32inch LCD 

Thanks,
~Jeff

---

### Post by CharmyBee on 2009-04-20
You can edit UT2004.INI and explicitly specify resolutions. Look for these in there:

```
[SDLDrv.SDLClient]
WindowedViewportX=640
WindowedViewportY=480
[b]FullscreenViewportX=800
FullscreenViewportY=600[/b]

```
Change those values accordingly to the resolution you want (preferred native res of the screen)

---

### Post by beastrace91 on 2009-04-20
You know, I can't seem to find a ut2004.ini file anywhere, where should it be at in my file system?

~Jeff

---

### Post by Cappy on 2009-04-20
> **beastrace91 said:**
> You know, I can't seem to find a ut2004.ini file anywhere, where should it be at in my file system?

~Jeff

> ~/.ut2004/System/UT2004.ini
I think.

rlocate is useful for finding things like this quickly btw.

---

