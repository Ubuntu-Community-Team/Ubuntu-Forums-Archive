---
title: "wine opengl winmm Penumbra"
date: 2006-06-25
forum: Gaming &amp; Leisure
---

### Post by pau on 2006-06-25
I'm trying to play to Penumbra but everything was crashing. I thought it was becasue of arts. When I tried to launch winecfg and go to sound it was crashing so that I renamed

```
/usr/lib/wine/winearts.drv.so
```

But now the problem is that wine crashes after setting a wrong screen resolution and "says"

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd4ccf0)->((nil),00000008)
fixme:opengl:wglChoosePixelFormatARB unused pfAttribFList
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

any hint?

---

