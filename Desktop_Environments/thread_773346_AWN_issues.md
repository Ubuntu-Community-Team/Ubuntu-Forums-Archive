---
title: "AWN issues"
date: 2008-04-28
forum: Desktop Environments
---

### Post by Mchl923 on 2008-04-28
I have AWN installed (avant window navigator) and it was all cool until I installed some themes and now whenever I maximize a window, the icons on the dock go up from the bottom and the "maximized" window's bottom border is about and 1.5 inches from the bottom of the screen.
youtube video:
[http://www.youtube.com/watch?v=3eb_hiYyW1E]("http://www.youtube.com/watch?v=3eb_hiYyW1E")

any help?

---

### Post by moonbeam on 2008-04-28
We're currently trying to determine what is causing this issue.  It might also be  good to subscribe to it as when a solution is found that's were it will be posted.

We (awn devs) would appreciate if you could make a comment in this bug:

[https://bugs.launchpad.net/awn/+bug/222300](https://bugs.launchpad.net/awn/+bug/222300)

Please indicate distribution, version etc.  Also of particular interest are the video drivers in use and window manager.

I'm also going to suggest a recursive unset on of your awn gconf settings...  I'll post instruction in the bug itself in a few minutes.

Thanks,

---

### Post by Mchl923 on 2008-04-28
Thanks moonbeam,
```
gconftool-2 --recursive-unset /apps/avant-window-navigator
```
works perfectly

---

