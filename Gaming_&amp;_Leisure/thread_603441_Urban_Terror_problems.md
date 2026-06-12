---
title: "Urban Terror problems"
date: 2007-11-05
forum: Gaming &amp; Leisure
---

### Post by popacsek on 2007-11-05
Hi,

I have recently installed  Ubuntu 7.10 on my home box, and I experienced some problems with urban terror 4.0.
After a few minutes the game switches from full-screen mode to windowed mode. After that it doesn't accept any keyboard or mouse input! Only I can do is Ctrl-Alt-Backspace ...
The second problem is that the game is much smoother under gentoo, however I use older kernel and nvidia driver under gentoo than under ubuntu!

I have tried these on an another machine, and I expreienced the same problems.

Any idea? Have the same problem?

---

### Post by FG123 on 2007-11-05
Yup, me and at least one other guy (so probably more people too) have experienced the same problem.

The fix is quite simple: disable Compiz before running the game. Apart from running a bit faster it's guranteed to stop this fullscreen to windowed-lock-up-the-system thing from happening. At least I've never had it happen after doing so.

You can disable compiz by pressing Alt+F2 and typing in

**metacity --replace**

and re-enable it using

**compiz --replace**

afterwards. There are other ways to disable Compiz automatically, or you could just make some launchers on the panel which run these commands. Either way, that's your problem.

---

### Post by popacsek on 2007-11-05
Thank You, I will try it at home.
And what about the smoothness? When I turn around in the game, it is like an old 10 FPS movie, however the average FPS is between 50 and 90.
May be  I should build a custom kernel ...

---

### Post by strik9 on 2008-02-25
try disabling your screensaver, or just set it to where it wont come on 2 hours.

---

