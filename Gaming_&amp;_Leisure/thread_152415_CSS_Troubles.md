---
title: "CS:S Troubles"
date: 2006-03-29
forum: Gaming &amp; Leisure
---

### Post by gaberade on 2006-03-29
Well I figured out how to get Steam working with wine. I've got tahoma fonts, the mozcontrol .dlls, and what I assume to be the proper video card drivers. I was able to actually download CS:S. The problem occurs when I try to launch CS:S. My screen adjusts it's resolution and the CS:S loading screen comes up. Then CS:S closes, but my resolution remains changed and steam is still running.

Console spits out a ton of fixmes. I can post exactly what comes out if anyone needs to see it, but it's quite long.

anyone have any ideas?

---

### Post by ispmarin on 2006-03-29
Did you try with cedega? Or you try to adjust the resolution of you X with Crtl+Alt+Minus to match the CS, and sees if that works, or even edit the xorg.conf to match the game resolution (not very practical...).

---

### Post by gaberade on 2006-03-29
[QUOTE=ispmarin]Did you try with cedega? Or you try to adjust the resolution of you X with Crtl+Alt+Minus to match the CS, and sees if that works, or even edit the xorg.conf to match the game resolution (not very practical...).[/QUOTE]

Well I tried launching steam with a bunch of extra commands:
WINEDEBUG=-all wine Steam.exe -console -width 1280 -height 800 -applaunch 240 -heapsize 128000 &

Same thing is happens but it takes longer for cs:s to close itself.

---

