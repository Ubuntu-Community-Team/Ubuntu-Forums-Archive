---
title: "WoW crashing"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by FKi on 2007-06-01
i followed the guide from [http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

and i had it installed and started to work on some of the patches, i got to about patch #2 when i remembered some steps from the guide i missed, just the step that modified the wow wtf file, and so i changed it, when the patch was installed, i ran it and it said something like "your driver doesnt support this"

{now i should of told you this before but here goes, i had vista on this system and when i ran it on vista, i would play for about a minute ,and all the suddon it would freeze, and black screen, then continue playing. (very anoying).  }               

so i went back into that file and restored it original settings.. so here i am starting the game up so i can continue my patching.  and it black screens..........you see your mouse for a few seconds...........freeze........and continues.

so what could be wrong? vista froze, ubuntu freezes, do i just need to get a new vid card?

---

### Post by Sammi on 2007-06-01
Systems specs please.

Cpu, ram, graphics card...
Graphics card driver version...
Wine version...

And please run this command in a terminal and post the text output:
```
glxinfo | grep rendering
``` And let this command run for a while, say 30 seconds, then post the output:
```
 glxgears -printfps
```

---

### Post by Colro on 2007-06-01
If it crashed in Vista as well then you might want to ask in WoW's tech support forums about it, if it is video card related they may have a fix for it that won't require you to run off and spend $200.

---

