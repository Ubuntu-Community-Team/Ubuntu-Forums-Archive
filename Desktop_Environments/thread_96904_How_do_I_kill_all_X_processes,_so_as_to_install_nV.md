---
title: "How do I kill all X processes, so as to install nVidia drivers?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by handy on 2005-11-29
Hi,
Yep, I'm obviously a nOOb,

The title says it all, I don't know the command to kill "X", as close as I can get is:

Ctrl-Alt-Backspace

Which quickly takes me through the pre - X shell then back to the graphical log in screen!?

When I kill X, then I can try to install the nVidia drivers for my 6800 GT, then I can try the UT2K demo, & see just what this linux setup can do. 

Thanks for your time,

handy

---

### Post by az on 2005-11-29
Here are three ways:

1.  Boot into recovery mode.

2.  From the desktop run 
init 1
in a terminal

From either of these options, type
init 2
to restart the desktop.

3.  From the desktop, hit CTRL-ATL-F1, log in and typ

sudo /etc/init.d/gdm stop

To restart it, ty
sudo /etc/init.d/gdm restart

---

