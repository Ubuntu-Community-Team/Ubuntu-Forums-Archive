---
title: "What VNC viewers are available?"
date: 2009-01-16
forum: General Help
---

### Post by diablo75 on 2009-01-16
I seem to remember that back in the days of 7.04 (or so) the command "vncviewer" in the terminal seemed to load a different viewer that the one that is the default viewer now.

The most distinct difference that I've noticed is that the menu that appears on screen when you press the F8 key contains far fewer options than the one I used to use.  I conduct a lot of reverse VNC sessions where I'll enter the command "vncviewer -listen" and someone else will run "x11vnc -connect [my dyndns address]" to "toss" their desktop to my screen so I can fix a problem on their computer.

This VNC viewer that I've been using lately has some quirks that I don't like:

- It seems to enable mouse-keys on my PC after a session has ended for an unknown reason (although it is a known bug that's been around for over 5 years if you go by the [comments on launchpad]("https://bugs.launchpad.net/xorg-server/+bug/192508/comments/19")).

- Sometimes after a session has been killed from their end, VNC fails to quit on my end and remains in listen mode (which is a huge problem if I happened to be in fullscreen mode).  Hitting F8 to bring up the menu to kill the viewer sometimes produces no menu at all.  Every so often it seems like the only way I can truly kill it is by hitting CTRL-ALT-BKSP and log out of Ubuntu completely, I often don't have that option available to me if I happened to have VNC'ed into my own computer from some other location so I could accept their x11vnc -connect while I'm away from home.

- The other viewer simply presented me with more options when I hit the F8 key.  I don't remember what they were, but I also don't remember having any of the above quirks occur while using it.

So I'm just wondering if anyone knows what other viewer I might have been using.  The one I use right now produces this menu when I hit F8:

[IMG]http://linuxgazette.net/102/misc/washko/vnc_f8menu.png[/IMG]

And the one I used to use produced a menu that was close (if not the same) as this:

[IMG]http://www.redhat.com/magazine/006apr05/features/vnc/figs/vnc1-viewermenu-en.png[/IMG]

---

