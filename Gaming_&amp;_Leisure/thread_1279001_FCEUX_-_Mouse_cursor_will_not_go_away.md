---
title: "FCEUX - Mouse cursor will not go away"
date: 2009-09-30
forum: Gaming &amp; Leisure
---

### Post by codefenix on 2009-09-30
Hello, good people.

I am setting up FCEUX to work with Wah!Cade, goal being to use it in an arcade cabinet.  Overall, everything is working really well.  Curiously, I get no sound when using the GFCEUX frontend, but I do get sound when executing from Wah!Cade.  Strange, but I digress.

One major, yet benign little annoyance is that the mouse cursor appears in the middle of the screen when executing a rom in fullscreen.  I have looked through the fceux.cfg file, and it does not look like there's an option for toggling the mouse cursor visibility-- then again, maybe I just don't know what to look for.

I tried installing FCEUX using the deb package at [http://fceux.com/web/htdocs/download.php](http://fceux.com/web/htdocs/download.php), and then compiling from source using the instructions at [http://ubuntuforums.org/showthread.php?t=971455](http://ubuntuforums.org/showthread.php?t=971455) (incidentally, several users in this thread report the same problem, which apparently remains unresolved).

Some Google searching led me to a tool called Unclutter ([http://ubuntu-tutorials.com/2008/07/07/auto-hide-your-mouse-pointer-when-idle-with-unclutter/](http://ubuntu-tutorials.com/2008/07/07/auto-hide-your-mouse-pointer-when-idle-with-unclutter/)), which seemed like a good workaround.  Unfortunately, while it works on the Ubuntu desktop, the mouse cursor remains present during a fullscreen rom in FCEUX.

Has anyone had success solving this, or have any ideas?

---

### Post by BoyOfDestiny on 2009-09-30
I had run into a similar bug with mednafen about a year ago. However, I am fairly sure X11 or my intel drivers at the time were to blame.

The problem is gone for me in the current Ubuntu alphas (I've been running karmic for several months.)

The only other workaround I had found was disabling hwcursor in my xorg.conf (that option is since completely gone from the intel driver, so they definitely fixed it. I just looked right now.)

The best advice I can give if you don't want to upgrade your Ubuntu is, whip the mouse cursor to a corner while it can still move, so just as you are going full screen.

But really, updating might the best route.

---

### Post by codefenix on 2009-10-01
Thanks for the reply, BoyOfDestiny.

> The best advice I can give if you don't want to upgrade your Ubuntu is, whip the mouse cursor to a corner while it can still move, so just as you are going full screen.First, sorry if I mislead you (and any other readers) to think my problem is the cursor being "locked" in the middle of the screen.  I can actually move it just fine.  The issue is the fact that it keeps showing up "on top" each time a rom is loaded, and it will become irritating to constantly whip the trackball after a while.

Second, upgrading Ubuntu isn't completely out of the question for me.  Do you think the upcoming 9.10 release would address any issues with the drivers or X11?

---

### Post by codefenix on 2009-11-04
I upgraded to 9.10, and the mouse cursor is still on top of FCEUX.

So I am trying Mednafen, and as of yet I do not have this problem.  I think I actually like it better overall-- Vsync seems to be much better implemented.

Glad to learn about Mednafen.  Seems to be a well-made, but underhyped project.

---

