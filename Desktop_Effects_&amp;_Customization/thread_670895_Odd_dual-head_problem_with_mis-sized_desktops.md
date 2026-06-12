---
title: "Odd dual-head problem with mis-sized desktops"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by chewd on 2008-01-17
Okay, I ended up solving my own problem here, i just thought i should post it somewhere in case someone else has the same problem, also to report this odd bug.

Im running 2 CRT monitors on a geforce 6600, & after fiddling around i did get them both working... however i noticed that whatever screen resolution i set it for, the desktop was always set for a higher size.

When i set it for 1024x768 screen res, it would give me 1280x1024 desktops, the screen would pan around when you moused to the edge of the screen.

Furthermore when i cranked up the screen res to 1280x1024, i would get an even bigger desktop.... No matter what screen res i set it for, the desktop size was always one size higher, always resulting in the pan & scan virtual desktop nonsense.

It drove me nuts for 2 days!

Heres how i ended up solving the problem.

In screens and graphics, instead of using for example "monitor 1280x1024" i chose "LCD panel 1280x1024" and everything works fine.

So.. to review

monitor 1280x1024 = odd problems with mis-sized desktops
LCD panel 1280x1024 = everything works like it should

As i said both my monitors are CRT's... seems odd that i have to lie & tell it theyre LCD panels... but who cares as long as it works!

Anyway... hope someone finds this useful.

---

### Post by rune0077 on 2008-01-18
You can just scroll all the way to the bottom of the list, and set it as Plug n' Play monitor, that'll give you all possible resolutions.

---

### Post by chewd on 2008-01-18
Plug N play monitor was the default... & was only giving me 800x600 with dual head.... but then maybe that was before i setup the nvidia driver... im not sure.

I did, at one point, tell it what monitors i actually have, & still got the pan & scan.

Anyway, no biggie, just thought id post in case someone else was fighting the same prob.

---

### Post by PinkFloyd102489 on 2008-01-18
Open your xorg.conf and set Xinerama to false. The restart X. I had the same problem a few days ago and that seemed to fix it.

---

