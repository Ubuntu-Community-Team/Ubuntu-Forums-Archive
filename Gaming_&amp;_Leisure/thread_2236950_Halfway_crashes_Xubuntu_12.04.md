---
title: "Halfway crashes Xubuntu 12.04"
date: 2014-07-29
forum: Gaming &amp; Leisure
---

### Post by DirtDawg on 2014-07-29
So I bought [Halfway]("http://halfwaygame.com/") today, but during the second mission, the game crashes and my system locks up (cannot alt+ctrl+F1 out). The same crash happens if I run the game in WINE at the same spot.

I did manage to get an error message at some point that read:
```
intel_do_flush_locked failed: Input/output error
```

If I run the game using:
```
LIBGL_ALWAYS_SOFTWARE=1 ./Halfway
```
the game runs and will not crash, but is incredibley slow (like 3 fps), uses 187% cpu and heats my computer up quickly.

I think it may be a hardware problem or kernel bug concerning the Intel integrated graphics chipset and Ubuntu 12.04.

I wrote the devs for support, but I thought I would post here in case they can't help. 

If anyone is aware of a fix or workaround, I would love the advice. Thank you.

Specs:
Xubuntu 12.04
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
Integrated Intel set: Mobile GM965/GL960 Integrated Graphics Controller
3 Gigs ram

EDIT/UPDATE: The devs got back to me and were happy to try and help. It seems my suspicions were correct and the graphics chipset on this computer is just too poorly supported in 12.04, so there's little they (or I) can do to fix the problem. They were quick to respond and did offer a refund (which I declined).

With any luck, the problems will be patched out when I upgrade to 14.04!

---

### Post by Peter_Solver on 2014-07-31
Yes I think the problem narrows down to the graphics chip. You are using Intel GM965 Express Chipset. In my own opinion, the Intel HD Graphics 3000 is better. You can get ideas from here: [http://www.game-debate.com/gpu/index.php?gid=1205&gid2=582&compare=intel-gm965-express-chipset-vs-intel-hd-graphics-3000-desktop](http://www.game-debate.com/gpu/index.php?gid=1205&gid2=582&compare=intel-gm965-express-chipset-vs-intel-hd-graphics-3000-desktop)

---

### Post by DirtDawg on 2014-08-01
Right, well, if I had the ability to swap out the GPU, I would likely upgrade to something much more powerful. However, the computer is a laptop, so I work with what I have.

---

