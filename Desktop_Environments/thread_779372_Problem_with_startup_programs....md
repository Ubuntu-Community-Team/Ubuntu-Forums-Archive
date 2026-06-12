---
title: "Problem with startup programs..."
date: 2008-05-02
forum: Desktop Environments
---

### Post by fxguenea on 2008-05-02
HI, got an issue with the gnome-terminal and firefox... After entering my account's name and pass, when the desktop is displayed, firefox and one terminal are opened... Tried to fix it from the Sessions menu, but they don't seem like an option on the startup-programs menu...

Anyone got a clue?

Thanx

---

### Post by empthollow on 2008-05-02
have you checked the .xinitrc file in your home directory or the /etc/X11/xinit/xinitrc file?  These files start programs when X11 starts.

---

### Post by pietjanjaap on 2008-05-04
I got the same problem.The /etc/X11/xinit/xinitrc file is empty.

In ./gnome2/session, in the session file, there i found firefox(number 4).
All the number 4 i put a # before the line.
Now it's gone.

---

### Post by fxguenea on 2008-05-04
Now the problem has changed.. Since i worked with a text editor and the pidgin messenger those are the ones that appear running at start up...
does it still has something to do with the x11 file?

---

### Post by fxguenea on 2008-05-04
got this from the xinitrc file:

#!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

nothing to do with the programs right??

---

### Post by fxguenea on 2008-05-04
> **pietjanjaap said:**
> I got the same problem.The /etc/X11/xinit/xinitrc file is empty.

In ./gnome2/session, in the session file, there i found firefox(number 4).
All the number 4 i put a # before the line.
Now it's gone.

Got it fixed with that... thanx... 

PD: it's ~/.gnome2/session by the way...

---

