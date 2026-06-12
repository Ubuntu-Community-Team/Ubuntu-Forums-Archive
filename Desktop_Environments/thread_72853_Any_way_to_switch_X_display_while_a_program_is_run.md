---
title: "Any way to switch X display while a program is running?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by Whatsisname on 2005-10-07
Greetings

Is there any way that an application can have its X display changed while it is running?

Example:
I'm at home, and I have an open window such as azerues. I go somewhere else, and SSH in with X11 forwarding. Can I 'grab' that window and bring it to the new display, then before terminating the SSH session send it back, without terminating and restarting the program?

Thanks.

---

### Post by aysiu on 2005-10-11
I really don't know much about stuff like this, but I do know there are desktop-sharing programs and such out there.

---

### Post by finer recliner on 2007-12-09
> **Whatsisname said:**
> Greetings

Is there any way that an application can have its X display changed while it is running?

Example:
I'm at home, and I have an open window such as azerues. I go somewhere else, and SSH in with X11 forwarding. Can I 'grab' that window and bring it to the new display, then before terminating the SSH session send it back, without terminating and restarting the program?

Thanks.

i also would REALLY like to be able to do this. i haven't figured it out yet. anyone have an idea?

I know i could use VNC, but i dont need to view my entire desktop. SSH is much more suitable.

---

### Post by defaulk on 2008-06-01
Old thread, but I just had this same question.  Any new info?

---

### Post by alguin2 on 2008-06-01
I've solved that problem (sort of) with TightVNC, which is basically an in-memory X server that can be (re)displayed by any VNC client. 

I know that it's possible to have an app switch displays, but I'm not so sure that it can be done generically without the program knowing it. If, for example, an X [client] program retrieves server properties at some point during its initialization, switching to a different display with potentially different properties can make it fail.

I know of only 1 app that can switch displays:  Emacs.  To effectively switch displays, do:
1. Start emacs on display #1.
2. Do **ESC-x make-frame-on-display** (enter) , and enter X display #2.
   A window will open, in the second display. It's a clone of the first window,
   and anything typed on one window will reflect on the other.
3. Close the original window on display #1.
4. You've effectively migrated to another display.

---

