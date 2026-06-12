---
title: "Konqueror status bar - can it be hidden?"
date: 2006-01-04
forum: Desktop Environments
---

### Post by psrin on 2006-01-04
Hi all,
Can the status bar (the bar at the very bottom of the window that shows messages and certain icons) in konqueror be hidden? I'd like to maximize my screen real estate.

TIA.
Praveen

---

### Post by hotweiss on 2007-11-26
I have the same question?

---

### Post by Whiffle on 2007-11-26
Yep, although there isn't a GUI for it.

open up
~/.kde/share/apps/profiles/webbrowsing

and add the line:
ViewT0_ShowStatusBar=false


In the section marked [Profile].

Speaking of which, konqueror can be pretty friendly on screen real estate.  All I've got on mine is one bar at the top and one on the left.  Works nicely.

---

### Post by hotweiss on 2007-11-26
Thanks. For me webbrowsing was in /.kde/share/apps/konqueror/profiles

How did you get one bar at the top? If I hide the menu, it comes back each time I restart Konqueror...

---

