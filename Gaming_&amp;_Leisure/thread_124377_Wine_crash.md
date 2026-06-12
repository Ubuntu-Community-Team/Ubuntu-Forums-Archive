---
title: "Wine crash"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by fuggii on 2006-02-01
Hello 

I have problem whit setup some apps on wine 0.9.6 when i try to setup one of apps i have this error

```
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fdb3820)->((nil),00000008)
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 16
err:opengl:X11DRV_ChoosePixelFormat glXChooseFBConfig returns NULL (glError: 0)
```

And i dont really know how to fix this. Meybe someone have solution on this problem ??

Regards
fuggii

---

### Post by seth0x2b on 2006-06-10
I'm gonna *bump* this thread because I kinda' get the same error when I'm trying to run Diablo II:
```

seth@orion:/media/hdb1/games/Diablo_II$ wine Game.exe
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 t o 8
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd83570)->(0x700b4,00000 411)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 t o 16
seth@orion:/media/hdb1/games/Diablo_II$

```  I've never had this error and I played Diablo II on Hoary alot! Seems my move do Dapper is not without consequences :).
I've searched the forum for about 1 hour and I've seen that it's a known issue, but I couldn't find a solution.

Thanks alot.
Cheers

---

### Post by seth0x2b on 2006-06-11
I "apt-get remove'd" WINE (0.9.15), reinstalled it, and it's running really nice now, no more errors.
So...if anyone has the same problem, they might try reinstalling WINE.

Cheers

---

