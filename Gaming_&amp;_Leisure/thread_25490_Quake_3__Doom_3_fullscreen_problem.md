---
title: "Quake 3 / Doom 3 fullscreen problem"
date: 2005-04-10
forum: Gaming &amp; Leisure
---

### Post by efbie on 2005-04-10
Hello, i have a desktop resolution of 1400*1050 and when i play any idsoftware game, the fullscreen mode is broken. It displays the game in the left inferior corner at the set resolution, and the rest of the screen is filled with strange things.

I have a radeon M9600 and the ati drivers. otherwises the games works fine.

---

### Post by efbie on 2005-04-10
I think it has to do with the fact that i can't change my screen resolution.
If i try, it says Xrandr not supported by X11.

Does anyone know how to solve that ?

---

### Post by skoal on 2005-04-10
It sounds like you have a different issue than most who tried getting to run Doom3 on Linux, and that was enabling 24-bit depth color.  It does sound like it's just that particular resolution you're trying to run Doom3.  I've never used that particular screen resolution before.  

Why is it that you can only use 1 screen resolution?  Do you have multiple screen resolutions listed in your X config file?  Like:

Modes       "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

---

### Post by efbie on 2005-04-10
No there was only "1400x1050" but now i added other modes and it works fine ! thanks :)
But i just noticed that sound doesn't work in quake3. Is there anything special to do ?

---

### Post by nickless on 2005-04-18
I have the same Problem. :(
Also Quake always changes my resolution, when I quit. No idea why...

---

### Post by manny on 2005-04-18
[QUOTE=nickless]I have the same Problem. :(
Also Quake always changes my resolution, when I quit. No idea why...[/QUOTE]
 Did you guys use 1.32 "B" patch? No sure but it may help, my sound is working fine, (SB Live) Quake III changes my resolution when I quit sometimes, i have to ctl alt - (minus) or + two or three times to get my res back. but if i delete other res in the X config it seems ok, need some more testing

---

### Post by nickless on 2005-04-18
Yeah the patch is the right one :)
didn't knew that changing the res is so easy :D thx

---

