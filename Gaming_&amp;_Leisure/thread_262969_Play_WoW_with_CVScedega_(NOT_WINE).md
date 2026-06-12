---
title: "Play WoW with CVScedega (NOT WINE)"
date: 2006-09-22
forum: Gaming &amp; Leisure
---

### Post by M4C C41N on 2006-09-22
Hi all, I want to play WoW with cvscedega (not with Wine because I can't : see my other thread [here]("http://www.ubuntuforums.org/showthread.php?t=261625")).
I installed WoW, but at the end of the installation I get a 132 error.
When I launch WoW with "sudo cvscedega WoW.exe", I get these messages in my terminal : 

```
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=787428
err:ddraw:Direct3DDevice9_GetStridedDataUP stride inconsistency! 36 != 24
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=787572
err:ddraw:Direct3DDevice9_GetStridedDataUP stride inconsistency! 36 != 24
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=787716
err:ddraw:Direct3DDevice9_GetStridedDataUP stride inconsistency! 36 != 24
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=787860
err:ddraw:Direct3DDevice9_GetStridedDataUP stride inconsistency! 36 != 24
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=788004
err:ddraw:Direct3DDevice9_GetStridedDataUP stride inconsistency! 36 != 24
fixme:ddraw:Direct3DDevice9_SetStreamSource offset=788148
```

and the game looks like this :


[[img]http://www.hiboox.com/vignettes/3806/ec5d2be9.png[/img]](http://www.hiboox.com/image.php?img=ec5d2be9.png)

Have someone an idea plz ?

---

### Post by M4C C41N on 2006-09-22
It worked when I change my config.wtf to 

```
SET gxApi "opengl"
SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```

but I updated my wow and now I get that error message : "err:opengl:wglGetProcAddress Extension glFramebufferTexture3DEXT defined in the OpenGL library but NOT in opengl_ext.c... Please report!
"

---

