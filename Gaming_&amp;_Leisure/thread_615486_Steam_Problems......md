---
title: "Steam Problems....."
date: 2007-11-17
forum: Gaming &amp; Leisure
---

### Post by au_vagabond on 2007-11-17
Hey all,

I realise that Steam issues are hardly irregular with wine, but I can honestly not find anyone with the same problem as me (I apologise in advance if this isn't the case and I'm just being an idiot). Basically, steam works fine until I try to run a game - which basically defeats the purpose imo. Hence, I'm begging you for help. I have steam community turned off, and I have an intel core 2 duo 2.16, 1500 (ish) of DDR2 667 ram. 
 The error I've been getting in a little pop-up window is:

"Steam.exe (main exception) : Win32 Structured Exception at 7AAC367A : Attempt to read from Virtual Address 0 without appropriate access rights"

Thankyou to all that help. 

Vags

---

### Post by Colro on 2007-11-17
See if this helps:

```
rm ~/.wine/drive_c/Program\ Files/Steam/ClientRegistry.blob
```

...or just delete your clientregistry.blob file in your steam folder on your own. This'll reset some of your steam settings, but it should fix your problem.

---

