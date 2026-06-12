---
title: "resizing emacs freezes desktop"
date: 2009-07-29
forum: Desktop Environments
---

### Post by cjames53 on 2009-07-29
If I start emacs and try to resize the window, Ubuntu (Gnome) freezes completely.  The cursor remains in the "resize" state (a little corner-of-window icon).  Emacs appears to have grabbed the focus and will not release it.  If I ssh from another computer and kill emacs, everything returns to normal.

This is highly repeatable.  Emacs is completely unusable because of this.  It worked until recently.

This is Ubuntu 9.04, all packages updated.  The display is an ATI Radeon using the most-recent driver from AMD.

---

### Post by tobi83 on 2009-08-07
..just to confirm, i have the excact same problem!

And a hint so you don't have to run to your neighbor 's computer everytime : it works for me to log on as a new user (strg+alt+F1), kill emacs and exit!

I'm using Ubuntu 9.04 and Emacs 22.2.1.

---

### Post by cjames53 on 2009-08-12
Isn't anybody working on this problem?  It is 100% reproducible, emacs is completely useless on my system.  I can't believe I'm the only one who has this problem.  EVERY SINGLE TIME I try to resize the emacs window, my screen freezes, completely.  The mouse turns into the resize icon, and you can move it around, but mouse clicks and keyboard input are ignored.  I can do the [Alt]-F2 and get a console, then kill emacs, at which point the system unfreezes.

---

### Post by tobi83 on 2009-09-05
Not the only one!

Now i installed emacs21 which doesn't seem to have this problem. 
Maybe that works for you too..

---

### Post by tty on 2009-09-10
I had the same problem. compiz.real goes at 100%.  By killall -9 compiz.real the problem was solved - somewhat (Not sure how to restart it correctly). In the meantime the problem is gone. I upgraded to Emacs 23 (from source) and compiz (1:0.8.2-0ubuntu16) karmic

---

