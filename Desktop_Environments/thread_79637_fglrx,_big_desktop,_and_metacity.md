---
title: "fglrx, big desktop, and metacity"
date: 2005-10-20
forum: Desktop Environments
---

### Post by ewhitten on 2005-10-20
I've setup the fglrx driver in my xorg.conf to be "Big Desktop," i.e. spanning both displays.

I have two 19" lcd's running at 1280x1024 each.  My only annoyance is that all dialog boxes and most new windows appear smack dab in the middle of what the window manager sees as one 2560x1024 screen.

Is there any way to have metacity always place the window in a certain location? I've seen patches to do this, but only on metacity 2.10 (breezy has 2.12).

---

### Post by objorkum on 2005-10-20
The newest fglrx (8.18.6) finally supports Xinerama, which metacity and others have support for (you will not have those problems with Xinerama).

So you need the latest drivers (should be a guide on the tips&tricks-forum), and and xorg.conf setup with Xinerama.

I can recommend this forum for help with fglrx:
[http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88)

Xinerama-info:
[http://www.tldp.org/HOWTO/Xinerama-HOWTO/](http://www.tldp.org/HOWTO/Xinerama-HOWTO/)

---

### Post by ewhitten on 2005-10-20
[QUOTE=objorkum]The newest fglrx (8.18.6) finally supports Xinerama, which metacity and others have support for (you will not have those problems with Xinerama).[/QUOTE]

ahhh.. much better.  Thank you!  I hadn't realized that new fglrx drivers were out, let alone now supporting xinerama.  

Now I just need to figure out why restarting the X server (by restarting GDM or Ctrl+Alt+Backspace) puts my displays into power save mode.  I can't see anything until I restart.

---

