---
title: "Vanishing window manager after Update"
date: 2011-07-13
forum: Desktop Environments
---

### Post by Python Jedi on 2011-07-13
Yet another problem, but I need some input here.  I just updated and restarted my computer (lots of updates), and when I logged in all of the window decorations are gone as well as alt-space and alt-tab doing nothing.  Thinking that the update messed with the WM settings, I opened the settings manager up, but both the Window Manager and Window Manager Tweaks section are blank.  The other sections are fine, just those two.  Any suggestions? (and no, I'm not doing Unity, KDE, or Gnome)  The panels appear to be functioning correctly, though my workspaces got smashed as well.

Edit: Upon closer inspection, I can no longer add workspaces, I set the number of workspaces to 4, but it only shows one in the list below

Edit 2: Upon creating a new user to mess with themes, the WM was working fine in the new user, same problems in this user.

---

### Post by Toz on 2011-07-13
xfwm4 has crashed. Restart it by Alt-F2 or running at the command prompt:
```
xfwm4 --display=:0.0 --replace
```You'll probably find that when you log in again, that you'll have the same problem. According to one of the xfce developers, here is the fix for this problem: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102") - see post #2.

---

### Post by Python Jedi on 2011-07-13
Thanks, that seemed to fix it, I loged out an logged in again, no problems.  I'll check that post anyway

Great help Toz!

---

### Post by Toz on 2011-07-13
Glad to hear it worked. Can you mark this thread as Solved from the Thread Tools link above?

---

### Post by Python Jedi on 2011-07-15
For ease of use, I just added a keyboard shortcut: ctrl+alt+del!  it was my goto when I used windows, and this is the worst thing I've had happen so far.  Thanks again!

---

### Post by Duncan Williams on 2011-07-15
slightly off-topic.
I did an update 2 days back, amongst a lot of other stuff was the new linux kernel.
Well that blew my nvidia drivers out the window and left me with no gui.
In the end I re-installed, did all the updates and re-installed my nvidia drivers.
All ok in the end, but, how do I update the next kernel without all that hassle?

---

### Post by goodbye-windows(tm) on 2011-08-15
I have the identical problem, except my failure didn't occur after an update. I have no explanation for why/what caused my problem.

My daughters account functions normally.

I did the fix with the command line as suggested by Toz. It fixed the problem in short order. It's so nice to be able to control my windows, especially the ability to resize and shut down the window again!!!

I rebooted my system, and the problem did not recur.

So, I'm a happy camper again.

Regards to all, especially those who contribute technical info and those who administer this forum.

Art

---

