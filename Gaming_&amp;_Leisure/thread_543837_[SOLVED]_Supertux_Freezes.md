---
title: "[SOLVED] Supertux Freezes"
date: 2007-09-05
forum: Gaming &amp; Leisure
---

### Post by sprogmeister on 2007-09-05
Supertux causes Ubuntu to crash every time I close it. It leaves me with a movable arrow but that is it,no controls work whatsoever! Can anyone help? Please bear in  mind I am very new to this

---

### Post by K.Mandla on 2007-09-05
Moved to Gaming & Leisure. ;)

---

### Post by disturbedite on 2007-09-05
i have the same problem, but i haven't been able to resolve it, so i don't use it in the meantime.

---

### Post by FuturePilot on 2007-09-05
Do you have the 3D accelerated driver for your graphics card installed? I think you need it for Supertux.

---

### Post by charlieg on 2007-09-05
Supertux Freezes?  Well, if he does choose to run around in snow... *snigger*

---

### Post by disturbedite on 2007-09-06
well, i have an intel i845g integrated chip, but i am using the intel (not i810) driver w/ direct rendering enabled, if that answers your question...

---

### Post by sprogmeister on 2007-09-14
It's just, I go to close the game and the whole computer hangs control-alt-esc won't even work.

---

### Post by peakshysteria on 2007-11-07
Updated my daughters Feisty to Gutsy last night using the alternate Gutsy Gibson CD. Everything went smooth. But upon starting Supertux the screen goes black. To come back we have to reboot.

Anyone encountered this problem? Havent tried to reinstall....might work....nice if anyone have experienced similar problems.

---

### Post by KIAaze on 2007-11-08
Have any of you tried running it from console to see the output?

If it crashes so that you have to reboot, try:
```
supertux > 1>supertux.log 2>&1
```

The console output will then be available in supertux.log (file located from where you launched supertux).

Do you have the same problem with other SDL games? (ex: Super Maryo Chronicles, Kobo Deluxe, Metal Blob Solid, etc)

Maybe you should try contacting the supertux developers.

---

### Post by sprogmeister on 2008-08-24
I just downloaded it again from Applications >> Add/Remove Programs and it worked great!

---

