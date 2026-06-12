---
title: "Wine with Counter-Strike CD"
date: 2006-08-06
forum: Gaming &amp; Leisure
---

### Post by billyfoxtrot on 2006-08-06
I managed to install Counter-Strike: Condition Zero using Wine, but now every time I try to run it by going into its directory and typing:

```
wine czero.exe
```

a message pops up saying "No CD-ROM drive found."

I used autodetect to assign the drives in winecfg, is there something else I need to do to run this game?

Thanks!

---

### Post by Stickittotheman on 2006-08-06
Well, I don't speak from experience (re-downloading ISO, this time from europe server... *sigh*), but I assume you have STEAM installed? And into the .wine folder? If so, WINE steam.exe, which should load steam just like in windows. Then, download CS:CZ, and exec it from the STEAM games menu. I don't actually know if theres a way do directly launch CZ, I think you might have to exec STEAM every time, and launch it from there.

---

### Post by HAARP on 2006-08-06
```
wine steam.exe -applaunch 80
```
launches directly into CZ.

---

