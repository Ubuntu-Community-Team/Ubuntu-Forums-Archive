---
title: "negative geometry position selects wrong side for some users"
date: 2018-09-24
forum: Desktop Environments
---

### Post by Skaperen on 2018-09-24
i am running Unity on Ubuntu 16.04.5 LTS with multiple users.

when  i have a script launch a program with a negative horizontal position in  the geometry option, it works fine in one user and places the script at  a horizontal position relative to the right side of the display as  intended..  this happens to be the user i needed it first in, so i  initially wrote the script under that user.  later i had another 3 users  copy that script over to their home directories (so that copy would be  owned by them.  but when i ran it, it placed the window relative to the  left side, plus a few more pixels to the right.

the intended  position was -1 so it would be just one pixel away from the right end.   but it ended up about 16 pixels from the left end.  the program is  "gnome-terminal".  when i intend to position it relative to the left  side, it always works on all users.  i usually have 12 logged in users  at a time, switching them as needed.

**does anyone have any idea why it would work right for one user and work wrong for another?**

---

### Post by again? on 2018-09-24
If it's in Unity it's may have to do with the number of virtual desktops for different users.
Do some tests using
```
wmctrl -d
xwininfo
```

---

### Post by Skaperen on 2018-09-24
all 12 users have 9 virtual desktops in a 3x3 arrangement.

---

