---
title: "Gnome panel frequent crashes"
date: 2005-10-25
forum: Desktop Environments
---

### Post by ChrisTheGeek on 2005-10-25
I'm having a frequent problem with the Gnome panel crashing on me when working in Nautilus.  

Everything is stable for about an hour and then the panel crashes (although how long it stays stable is very variable).  The problem is not repeatable i.e. it isn't one particular thing I do that causes it to crash.  Usually I only have nautillus, evolution and a terminal open.

When it crashes I'm given the message "The panel has quit unexpectedly" and offers me the choice of restarting it, closing it or informing the developers.

Unfortunately if I choose 'Restart' then it tells me a panel is already running and then I get the same panel error again in an infinate loop.  The computer then slows right down so that the GUI is unresponsive.  

If I click on 'Close' then the panel dies.  In this case the mouse is still responsive, the bottom panel still usually works and the open applications are fine.  To get the panel back though I have to restart gnome (ctrl+alt+backspace) since using 'killall gnome-panel' doesn't fix the problem.

As you can imagine this is extremely frustrating!  Is anybody else having this kind of problem?  Is there some log file I can copy here to help diagnose the problem?

Thanks,
Chris

---

### Post by uacciuari on 2005-10-25
Today morning I was having the same problem, and after a long search on the web I found a tip in this thread:

[http://ubuntuforums.org/showthread.php?t=14853](http://ubuntuforums.org/showthread.php?t=14853)

It's about 4.10 LiveCD, but it solved my issue with 5.10 (I have an i386 full install).

Joaoeb suggested to delete the file ".recently-used" from the user's home directory, and now everything's fine (forever, I hope...).

It doesn't fix the problem for everybody, but give it a try.

---

### Post by RandomGeek on 2005-10-25
Thanks for the reply. I've tried deleting the .recently-used directory but the problem persisted.

Is there an easy way to re-install gnome?  Does anybody think that would help?  The computer is basically unusable as it is and I'm getting really frustrated with it :(

---

### Post by ChrisTheGeek on 2005-10-26
Ok, I've tried disabling the NVidia drivers just to make sure it wasn't them causing the problem.  It wasn't, I'm still getting crashes all the time.

I'm considering swapping to KDE but I'm reluctant to do that since I much prefer the simplicity of gnome.  Can I somehow 'reset' gnome or reinstall it?

---

### Post by ChrisTheGeek on 2005-10-28
I've found a solution of sorts.

I decided to create a new user and do the same task whilst logged in as the new user.  The panel didn't crash on me.  This makes me suspect a gnome setting somewhere for the original user was the cause of the problem.

I'm now looking for a way to reset the gnome settings for the old user without loosing the program data such as Evolution.  I'm hopefull a bit of searching will find an answer.  I know about the .gconf, .gnome and .gnome2 directories in my home directory but I'm not sure if these can just be deleted or whether there is more to it.

---

