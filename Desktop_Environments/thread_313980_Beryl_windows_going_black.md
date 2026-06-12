---
title: "Beryl windows going black"
date: 2006-12-06
forum: Desktop Environments
---

### Post by rpkehoe on 2006-12-06
I am running Edgy with KDE and Beryl, and I am having windows going solid black for no particular reason.  It only happens when the windows are a certain size, if I resize them, the interior of the window appears.  This used to happen very occasionaly, but it seems to happening all the time now, especially with the gimp.

Anyone else have this?

---

### Post by Shatrat on 2006-12-06
This is a known problem with the nvidia beta driver and AIGLX.  
Once you run out of video memory for storing the textures of those windows, any additional windows you open will just be black.  For me with 128mb the upper limit is stil a lot more windows than I actually have open during regular use.
There's a thread about it on the nvnews linux forum if you want to search for it, I havent seen any ETA on when they will put a fix into the drivers for this.

---

### Post by 23meg on 2006-12-06
Try launching Beryl with the --force-aiglx and --use-cow options.

---

### Post by darkmediator on 2006-12-07
Do u have compiz installed also? If so remove it. I installed compiz after beryl and same problem started. Windows went blank, white, black etc.

---

### Post by rpkehoe on 2006-12-07
Thanks Shatrat, thats sounds like my problem.  Sounds entirely reasonably that I would run out of mem with multiple gimp windows open and Beryl.  I appreciate the help.

---

### Post by 23meg on 2006-12-07
I too have that problem; it's a known driver issue and --force-aiglx is the only workaround for now.

---

### Post by rpkehoe on 2006-12-07
Thanks, I'll give that a try.  I am stuck on an XP box at work now.

---

