---
title: "Windowing system went wonky"
date: 2014-07-20
forum: Desktop Environments
---

### Post by redder on 2014-07-20
Suddenly, my window manager (in Xubuntu 13.10) is misbehaving:

[LIST]
[*]No "chrome" on windows (like the close and resize buttons on the upper right)
[*]Alt-Tab does nothing
[*]No desktop icons appear
[*]When I move windows, they don't always allow the window under them to redraw
[*]The Google Chrome window, which is at a size that is about a third of the screen, cannot be resized.  
[*]Firefox freeze and won't repaint, while Chrome won't accept text input, during the time that they are loading a page.
[*]When I launch a terminal, it won't accept text input for about ten seconds.
[*]Restarting my computer doesn't resolve this.
[/LIST]

What happened to my windowing system? How can I fix this?

---

### Post by Toz on 2014-07-20
Its probably crashed. You can restart it with:
```
xfwm4 --replace
```
...but its probably best to clear your session cache (in case its corrupt) and log out and in again (with an blank session cache, Xfce will start up with all the default components enabled).

Go to Settings Manager >> Session and Startup >> Session and click on the "Clear Saved Sessions" button. Then during logout, make sure that the "Save session for future logins" checkbox is _unchecked_.

---

### Post by redder on 2014-07-21
Thank you! That solved the problem.

---

### Post by Bucky Ball on 2014-07-21
Nice work. Please mark the thread as solved to help others by following the second link in my signature. ;)

---

