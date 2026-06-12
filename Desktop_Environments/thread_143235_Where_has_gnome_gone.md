---
title: "Where has gnome gone?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by KiLLeR_WoMBaT on 2006-03-12
I just loaded and used Automatix.  It seemed to work perfectly.  My sound quit working.  Upon reboot I now cannot get gnome to start up.  Under the "session" button at the log in screen the only thing that works is "failsafe terminal".  Nothing else works; they all start to load and freeze with nothing.  I can ctrl-alt-bkspc to get back to the log in screen.

Please help me get my desktop back!

---

### Post by encompass on 2006-03-12
sounds like some funky changes happened in your profiles settings... hope out to a terminal... then try this:
goto the failsafe terminal...
type this... nuatilus
that will popup your nautilus program... from there do this..
find the hidden folders .gnome* and move them to a safe place in a new directory.
log out and log in... did you get in?  if so... some setting has changed in those files.. now from there I am not sure what happened in detail.  I am sure there is a log some where to figure that out.  but if you did not change too many settings you may just want to go from there and set you settings from there... otherwise... well.. you could try puuting back one dir at a time to find the problem area.  This is why I don't like using automatix to do things like this.  it can cause problems and you don't know what it did.
Hope that helps you get back logged in.

---

### Post by KiLLeR_WoMBaT on 2006-03-12
Okay, I tried that.  It did not work.  Again when I try to log in I get nothing but a blank screen and the mouse cursor.

One thing though.  In failsafe terminal mode, when I run nautilus my desktop background and icons come back.  When I exit it they disappear again.  

Non of the programs that I run in failsafe terminal mode have the window bars with "close", "minimize", "maximize".  Is this normal when you run things logged in a failsafe terminal session?

---

### Post by KiLLeR_WoMBaT on 2006-03-12
I got it back!  I'm not sure what did it.  I  used gdmsetup from the terminal and selected XCMCP to be enabled.  Then upon the next login I logged in remotely and it worked.

I'm going to reboot and see what happens.

---

