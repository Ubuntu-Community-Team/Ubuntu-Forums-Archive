---
title: "Disable panel expand doesn't work in Gutsy"
date: 2007-12-02
forum: Desktop Environments
---

### Post by kasio on 2007-12-02
Hi,

I have a panel on the bottom of my desktop, not expanded, and it holds launchers.

Whenever I start a new session, it is right in the middle of my screen.

To fix it temporarily, I have to expand it, then disable expand.

I have tried saving session, but to no avail.

Can anyone help me?

Thanks,
Kasio

---

### Post by kasio on 2007-12-02
There are numerous postings about the gnome panel expand option, yet noone has replied.

This is a BIG problem:

[http://ubuntuforums.org/showthread.php?p=3878037](http://ubuntuforums.org/showthread.php?p=3878037)

---

### Post by anaconda on 2007-12-02
Hmm.. I thought that this bug was already fixed. anyway here is one way to fix it:

Type in terminal:
```
gconf-editor
```
and from there go to: 
apps>panel>toplevels>bottom_panel_screen0
(I assume the name of that panel is "bottom_panel_screen0") If it isn't then substitute the real name in its place.)

and from there adjust the "y" to be what you want.
eg. I have 1280x1024 screen and my panel is 24pixels thick, So the "y" is 999..

This will make the panel work correctly after reboots.. atleast untill the next time you change your resolution to a smaller one and back to normal..

---

### Post by anaconda on 2007-12-02
I replied to the thread you gave..

I thought that this bug was already fixed.. but obviously not..

---

### Post by kasio on 2007-12-02
Thank you SO much! Tried looking through there, but never thought of that. Gr8!

---

