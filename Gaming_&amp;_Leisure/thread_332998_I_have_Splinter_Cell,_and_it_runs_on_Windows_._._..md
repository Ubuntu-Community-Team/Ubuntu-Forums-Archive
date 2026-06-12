---
title: "I have Splinter Cell, and it runs on Windows . . ."
date: 2007-01-06
forum: Gaming &amp; Leisure
---

### Post by CheshireMac on 2007-01-06
Hey folks. I've got Splinter Cell, and it runs on Windows . . .I've never tried to run a game on Linux before . . .when I try to run the cd, it says it can't mount the selected volume . . .is this a problem with the game, or the cd-rom? I imagine that I won't be able to run it without VMWare, but I wanted to try.

---

### Post by The Noble on 2007-01-06
The reason the volume can't be mounted may be because of the CD protection, as I know the Splinter Cell series has some wicked Anti-piracy measures.  The only way I know to run windows games is by using wine (or cedega), and after taking a look on their site, splinter cell doesn't work well if at all, so you may be **** out of luck. Good luck if you do try, however.

---

### Post by CheshireMac on 2007-01-06
> **The Noble said:**
> The reason the volume can't be mounted may be because of the CD protection, as I know the Splinter Cell series has some wicked Anti-piracy measures.  The only way I know to run windows games is by using wine (or cedega), and after taking a look on their site, splinter cell doesn't work well if at all, so you may be **** out of luck. Good luck if you do try, however.

Wine may not work (Doesn't run CD-Rom anymore apparently), but VMWare with XP running would run fine . . .I'm just wondering if it's worth it . . . It would probably be the only thing I need XP for. ~LOL~

---

### Post by The Noble on 2007-01-06
As far as I know, 3d acceleration through vmware is still experimental and won't provide any good speed required for playing a game as advanced as Splinter Cell. You would need one hell of a machine to even run the game, and that's if vmware decides to cooperate. The best way to run Splinter Cell would be by dual-booting. Sorry.

---

### Post by pseudonym on 2007-01-06
I tried running Splinter Cell on Cedega when I had it, which handles copy protection better than wine. The installer loaded but crapped out as soon as you click 'Install'. I don't think this game will ever run on Linux, sorry to say.

---

### Post by Enverex on 2007-01-10
I'd not say that was true. Lots of games would have seemed that way going back a while but even games like Half-Life 2 work now. I'll try and get a copy of this game from someone and start bug-reporting the various issues if someone hasn't already (AppDB isn't the place for bugs). If you'd like to try again with Wine 0.9.29 though you may get further, remember that you'll need a NoCD patch.

Jump on FreeNode IRC to #winehq if you need a step-by-step guide with it or getting the bug reports.

---

### Post by stavpal on 2007-04-20
Hello, I have installed splinter cell in wine but when I try to run it I get:

```

stavpal@stavpal:~$ wine "c:\\Program Files\\Ubi soft\\Splinter Cell\\system\\splintercell.exe"
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

```

Is there a possibility to run it in wine? If I try to use the no-cd patch (replace splintercell.exe, it plays the intro and then exits to the desktop.

---

