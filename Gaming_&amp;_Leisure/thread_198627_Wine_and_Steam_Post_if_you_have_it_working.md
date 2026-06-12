---
title: "Wine and Steam: Post if you have it working"
date: 2006-06-17
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2006-06-17
I'm trying to get the Half-Life based game Natural Selection working on steam, but keep getting an error about vgui2.dll not loading when I launch steam.

Steps I've taken:

Setup mozcontrol under WINE's program files
Setup tahoma.ttf
Installed Steam using WINE

How did you do it? Post the steps required to get Half-Life working. Thanks!

---

### Post by eqisow on 2006-06-17
I've only been able to get HL2 running on Cedega, and even that was unplayable. However, it is actually fairly playable on the new version of Cedega. Granted, my specs are also well above the Windows recomended. (AMD64 3000+, 2GB RAM, GeForce 6800)

P.S. - My definition of playable is sustained 30 FPS on 1024 with medium texture/poly and everything else off.

P.P.S. - My FPS was around 100 in Windows at 1024 with everything except HDR on, so it's a pretty big performance hit.

---

### Post by eqisow on 2006-06-17
I just noticed you said Half-Life, not Half-Life 2. HL1 works flawlessly for me in both Wine and Cedega, since it's implemented in OpenGL.

Edit: Check the last post in [this thread]("http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=1917&forum=10").

---

### Post by ubu-for on 2006-06-18
[QUOTE=Curlydave]I'm trying to get the Half-Life based game Natural Selection working on steam, but keep getting an error about vgui2.dll not loading when I launch steam.[/QUOTE]

It's probably a Steam and not a HL or HL2 problem.

Do you start Steam from its directory? Open the Terminal and try this for HL2 (applaunche 240)!

```

WINEDEBUG=-all wine 'c:\Programs\Steam\Steam.exe' -fullscreen -width 1024 -height 768 -applaunch 240 -heapsize 512000
```

---

