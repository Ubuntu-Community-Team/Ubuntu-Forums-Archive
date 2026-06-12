---
title: "Unreal Tournament resolution too high"
date: 2006-05-29
forum: Gaming &amp; Leisure
---

### Post by mokojin on 2006-05-29
hi folks

I have install ut on my laptop (i810 driver) and the resolution of the game is so high that's unplayable. On game preferences it only appears 1 possisible resolution:  1280x1024, with SDL Open GL.

Any way to resolve this?

---

### Post by TheMadArab on 2006-05-29
Is your xorg.conf set to use other resolutions?

---

### Post by MetalMusicAddict on 2006-05-29
[QUOTE=mokojin]hi folks

I have install ut on my laptop (i810 driver) and the resolution of the game is so high that's unplayable. On game preferences it only appears 1 possisible resolution:  1280x1024, with SDL Open GL.

Any way to resolve this?[/QUOTE]
I dont have UT2004 installed now but look for your ut2004 file in the system file of the game. In windows its an .ini file you can edit with a text editor. Anyway find a similar file and open it in gedit (if using Ubuntu) and you should see some resolution lines I think about halfway down. Edit to suit. Sorry if Im vauge but Im working from memory. Wait are you using UT or UT2004? If it is just UT you should still find a like file.

---

### Post by ash211 on 2006-05-31
The file MetalMusicAddict is referring to is ~/.ut2004/System/UT2004.ini

Under [SDLDrv.SDLClient] you can change FullscreenViewportX and FullscreenViewportY to lower resolutions.  If you run UT2004 in a window, the variables to set are WindowedViewportX and WindowedViewportY.

---

### Post by MetalMusicAddict on 2006-05-31
Ahh.. There ya go.

---

