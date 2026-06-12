---
title: "Black Screen after XFCE login"
date: 2007-02-07
forum: Desktop Environments
---

### Post by likerice on 2007-02-07
relative newbie here.

i'm using xubuntu, edgy. when i login to my xfce session, the splash screen runs and then i'm taken to a completely black "desktop". mouse pointer is there. keybindings work. but otherwise nothing.

earlier today i installed the kubuntu-desktop package in order to check out kde, and everything went fine.

i logged out of kde, logged back into xfce, switched windows my windows theme (nothing drastic), noticed while i was doing that that my trash applet disappeared, then my system monitor disappeared, then conky quit. i logged out, logged in and... ... ...trouble.

any suggestions will be greatly appreciated!

---

### Post by ffxr on 2007-02-07
try pressing alt-f2..

and then running: xfce4-session, xfdesktop, xfce4-panel

one or all of them *should * get you going..

then ensure to save session settings on exit, so u'll get them back next time you log in...

---

### Post by likerice on 2007-02-07
> **ffxr said:**
> try pressing alt-f2..

and then running: xfce4-session, xfdesktop, xfce4-panel

one or all of them *should * get you going..

then ensure to save session settings on exit, so u'll get them back next time you log in...

thanks for the help.

alt-f2 seemed to do nothing. 

xfce4-session produces the same effect as logging in, ie a black screen with mouse-pointer.

xfdesktop flashes my former desktop (yay!) for a brief moment before going black. a number of errors are returned followed by this message:

[INDENT]** (xfdesktop:9126): WARNING **: Unable to initialise D-Bus. Some xfdesktop features may be unavailable.
_IceTransOpen: Unable to Parse address eybo
Segmentation fault (core dumped) [/INDENT]

xfce4-panel similarly flashes the panel before fading to black. the terminal states that it "Failed to open device."

any other ideas? anyone? please?

---

### Post by killerisation on 2008-03-20
I have the same problem, only the screen just shows the desktop background.  It happened after I altered something in the display/desktop/window manager settings though I'm not sure quite what.

---

### Post by x1a4 on 2008-03-20
That error you got states that dbus is not running.  XFCE needs dbus to communicate between the various components and applications.  Run **/etc/init.d/dbus** and see if that helps.  After running dbus run **xfce4-session** to start your session.

---

