---
title: "[SOLVED] Overlarge window titlebar and Pidgin UI after updating to LTS 18.04"
date: 2019-02-27
forum: Desktop Environments
---

### Post by katajanoksa on 2019-02-27
I found multiple locked threads about this issue but none of them had a solution for me: Window title font was not having noticeable impact, themes did not help, etc.

For some reason specifically Pidgin UI and window title bars were huge, but everything else was regular tiny on my laptop. I went through the tweak tool and found nothing.

Turned out this was caused by "screen scaling" - for some reason it only affects my window title bar and Pidgin's UI size. I suspect my earlier use of a different window manager that was no longer available has masked this issue for a while, and update mostly forced me to deal with it. 

I turned it off with a new item under regular Gnome settings > Screens > Scale, dropped it from 200% to 100% and restored normality. Yay!

Other solutions:
[https://ubuntuforums.org/showthread.php?t=2359608](https://ubuntuforums.org/showthread.php?t=2359608)
[https://ubuntuforums.org/showthread.php?t=1745156](https://ubuntuforums.org/showthread.php?t=1745156)

---

