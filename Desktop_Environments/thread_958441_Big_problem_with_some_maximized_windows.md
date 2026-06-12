---
title: "Big problem with some maximized windows"
date: 2008-10-25
forum: Desktop Environments
---

### Post by bartoz on 2008-10-25
Hi everybody..
I'm experiencing a strange though really bothering problem with some windows.
So far it happened a pair of times with firefox and every time with the print preview of openoffice calc.
What happens is that if the window is maximized the mouse pointer disappears inside the window (but it is still visible and works well on the title bar and the menu bar) and the whole screen begins to slowly drift to white.
The whole thing stops if I change viewport, open another window (for example a terminal) over the one that gives the problem and it is less bothering but doesn't disappear if I reduce the size of the window.
I tried both with and without compiz but the situation doesn't change.

I hope I've been clear and hope somebody could help.

Thanks.

---

### Post by bartoz on 2008-10-25
bump..

---

### Post by bartoz on 2008-10-26
Up..

---

### Post by bartoz on 2008-10-27
Bump..
I have really no idea how to fix this problem..
Noone has?

---

### Post by bartoz on 2008-10-28
last bump, next is desperation..
nobody ever had a similar issue?
nobody could help?

---

### Post by snova on 2008-10-28
That's the strangest thing I've heard in a long time, actually.

It's either a bug in the application, toolkit, X server, or video driver. Gosh, that only narrows it down to the entire graphical stack.

Sorry. Feel free to start getting desperate.

Oh, can you get a screenshot? You never know what it might help.

---

### Post by bartoz on 2008-10-30
> **snova said:**
> That's the strangest thing I've heard in a long time, actually.

It's either a bug in the application, toolkit, X server, or video driver. Gosh, that only narrows it down to the entire graphical stack.

Sorry. Feel free to start getting desperate.

Oh, can you get a screenshot? You never know what it might help.

Well, I didn't manage to get a meaningful screenshot, but I found out a (possibly) strangest thing.
If I change the metacity theme the problem disappears for some time and if I get back to the theme I used it re-appears at once. It comes back anyway after a short time, changing the theme fixes the thing just for a short while..
The issue doesn't seem to be related to a particular theme though..

..any ideas?

---

### Post by Licurgo on 2008-10-30
Bartoz:
Could you give us the output of dmsg ?

---

### Post by bartoz on 2008-11-01
As often happens, the solution is the simplest thing..
I struggled to understand what the software problem was and the problem ended in being an hardware one.
I tried with another monitor and magically everything is perfectly normal.

Many thanks to snova and Licurgo for their help.

---

