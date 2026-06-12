---
title: "start a program from a shell and have it load into X on :0"
date: 2009-03-02
forum: Desktop Environments
---

### Post by graysky on 2009-03-02
Basically, I'd like to know how to start a program from a shell and have it load up in an active X session.  Example: Intrepid box is running X on display :0 as per defaults with my user logged in.  I want to ssh into the box from another PC and run a GUI program like mplayer and have it appear in the :0 display.  Is this possible and if so, how?

Thanks!

---

### Post by albandy on 2009-03-02
First you should allow to use your display:
from a console in your gnome session type: xhost localhost
this will allow local connections from other tty's

now in your remote ssh session type:
export DISPLAY=:0.0

type for example xclock and look in your graphical session if a clock apperars in screen.

---

### Post by graysky on 2009-03-02
Excellent, this is just what I wanted.  Thank you!

---

