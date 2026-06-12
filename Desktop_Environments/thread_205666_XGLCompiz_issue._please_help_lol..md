---
title: "XGL/Compiz issue. please help lol."
date: 2006-06-28
forum: Desktop Environments
---

### Post by Patrick-Ruff on 2006-06-28
hey all, I've worked my *** off to get xgl/compiz working but there are STILL issues, here are the current issues...


All the windows and top bottom menu's (in gnome) seem to have a sort of a purplish outline... also, the window's don't seem to be rendering correctly yet again... I have to resize the window for it to render what exactly is going on then, and I have to resize it every time just for it to update the render.


also, I'm running an ATI X300 PCI Express 64MB Mobility, and I'm not entirely sure the drivers are working as they should be, I have 3d acceleration it seems but, some things just simply don't seem right.

please help if you have any idea's.

---

### Post by Patrick-Ruff on 2006-06-29
bump, been 21 hours guys...

---

### Post by Patrick-Ruff on 2006-06-29
ok so, I'm getting yet aonther error, it says  Unrecognised option -fullscreen

and when I remove that I get another one, unrecognised option -accel
etc.


help?

---

### Post by kpkeerthi on 2006-06-29
When you use 'words' as options shouldn't they be preceded with double hypens? I guess -fullscreen should be --fullscreen.

---

### Post by Patrick-Ruff on 2006-06-29
oic, I'll try that now

---

### Post by Patrick-Ruff on 2006-06-29
nope, it didn't work...

---

### Post by Patrick-Ruff on 2006-06-29
k, I figured out the root of the proble, it was leading to Xorg-air, not XGL. ok, so now, XGL loads under the driver 'ati' however, it has no 3d or 2d accelleration whatsoever. and no window decorations.. compiz doesn't load either, and it says no useable screens found. 

I changed it to fglrx, and it doesn't load at all, it has the loading icon and a grey screen before the selcome screen so... somethings really wrong here...

---

### Post by Patrick-Ruff on 2006-06-29
cmon you guys, your killing me here lol.

---

### Post by Anduu on 2006-06-29
Look here [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by Patrick-Ruff on 2006-06-30
dude, do you guys think I'm some kind of idiot or something? I've BEEN there, I;ve seen every compiz tuturial, I'll guarentee you this...

---

