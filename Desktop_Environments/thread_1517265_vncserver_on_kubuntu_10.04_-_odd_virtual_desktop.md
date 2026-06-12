---
title: "vncserver on kubuntu 10.04 - odd virtual desktop"
date: 2010-06-24
forum: Desktop Environments
---

### Post by ghamilton on 2010-06-24
Over in Networking ([thread=1516238]_this thread_[/thread]) I explain the saga of my recent upgrade to Ubuntu 10.04 and the odd behavior of the virtual desktop when running vncserver.

I have begun to suspect that the new feature in KDE that allows it to restore all the running programs after a system restart may also be responsible for this weird "desktop cloning" thing that happens when launching vncserver.

The other thing -- the "programs launch in the wrong display" issue -- is a real puzzle.  I can launch xterm and konquerer in display :55, but not konsole and Dolphin (if I *sudo dolphin* it will stay in the virtual session).  Some applications work in the virtual desktop session, others pop up in the real desktop session (display 0).  I don't have an exhaustive list.


What I used to have (under ubuntu Hardy) was a clear, graphically sharp rendition of my real desktop in the virtual session, a single xterm instance, and anything I launched stayed in the virtual desktop session.

What I get now is . . . weird.  (See the [post=9500857]_referenced thread_[/post] for xstartup details.)


I would appreciate any illumination you can cast on this.

Thanx.

---

### Post by ghamilton on 2010-06-25
Bump.

Still seeking insight into this.

A)  Why would this xstartup . . .
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec sh /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
# xsetroot -solid grey
# vncconfig -iconic &
# xterm -geometry 80x25+10+10 -ls -title "$VNCDESKTOP Desktop" &
# startx &

```
. . . cause a virtual KDE session that has 1) funky unreadable menu/icon fonts, 2) a "clone" instance of every program already running on the real (display 0) KDE session?

Why would KDE insist on launching some programs (e.g. Dolphin, Konsole) in the display 0 session, even when started from the display 55 session?

Why would some programs complain that RANDR is "missing" from the display 55 X session?

This problem is new with 10.04 and KDE 4.4.2 (Plasma).

Open to any suggestions.

****

---

### Post by ghamilton on 2010-06-25
Okay.

I can go into one of the xterm windows in the virtual screen (display 55) and run this:
```
sudo konsole
```
and the konsole window launches (as root) in the virtual display.

There are some complaints and error messages, but the window opens and behaves correctly, and I can su back to my own user name.

From there, I can launch dolphin and it, too, stays in the virtual display.

Funky workaround, very messy.

Not what I'm looking for.


****

---

### Post by ghamilton on 2010-06-28
Bumping this back into view.

It's turning out that some applications "run" in the virtual session, but not really.

Kmail, in particular, gripes about connections it doesn't have, and then just locks up, requiring a kill -9 to shut it down.

This is now more than an irritant.

It's actually interfering with work.

:frown:

Anyone?  A little help here?

****

---

