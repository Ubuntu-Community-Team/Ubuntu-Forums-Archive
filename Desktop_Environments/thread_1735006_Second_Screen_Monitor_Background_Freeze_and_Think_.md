---
title: "Second Screen Monitor Background Freeze and Think it's a Compiz issue"
date: 2011-04-20
forum: Desktop Environments
---

### Post by excetara2 on 2011-04-20
This happens randomly but when it does it persists for awhile. It has happened on multiple computers before that all have a second screen. The background freezes so if I close a window. The image of the window remains even if it was closed. Or if a window is dragged across it. It shows the window like 30 times. dragged across.

How do I reset compiz to maybe correct this (or just reset the displays it remembers. I think it would totally reset if it didn't auto-recognize the display)? Or does anyone have any suggestions? Obviously if I run metacity --replace. The issue is fixed but then I can't use compiz. Then if I restart compiz after this the issue is still there. Even after resets or pulling the screen etc...

---

### Post by Bumfun MC on 2011-08-07
Same problem for me. But everything works with metacity.

---

### Post by excetara2 on 2011-08-07
I had figured this out but can't remember now. Yeah, it's an issue with compiz but keep trying because mine works fine now.

---

### Post by excetara2 on 2011-09-27
Happened again. Seems to fix it if you boot into failsafe gnome and then:

rm -r .compiz

which just holds session information. If I do that seems to fix the issue.

Cheers

---

