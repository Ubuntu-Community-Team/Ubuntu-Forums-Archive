---
title: "panel menu won't open"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Thunderdome on 2006-08-05
As usual, I apologize if the information I am looking for is located on this forum already...cause I sure can't find it.

PROBLEM:  I've got a fresh install of xubuntu going and for whatever reasons, my system panel menu won't open. It used to open...I mean...everything was working great for a few minutes.  Now nothing.  A tiny lil dot appears below the menu button when I click it, and that's it.  When I right click on the button, the 'Xfce Menu' option is greyed out.

Any help would be greatly appreciated as this computer is to be a birthday present for someone and time is running out.

---

### Post by sawjew on 2006-08-06
This is a known bug, I had the same problem.  Make sure your system is up to date and there may be a bug fix in the updates.  If updating doesn't fix it, open a terminal and copy this in;
```
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml
```

That will copy the default menu into your home directory as a user menu.

---

