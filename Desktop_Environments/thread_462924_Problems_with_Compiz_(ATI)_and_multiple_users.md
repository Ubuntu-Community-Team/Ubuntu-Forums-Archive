---
title: "Problems with Compiz (ATI) and multiple users?"
date: 2007-06-03
forum: Desktop Environments
---

### Post by khughitt on 2007-06-03
Hi,

I recently added a couple of users to my machine so that other family members could log-in and have their own personalized desktop. I am running compiz as my window manager (ATI), and this works fine for me but I cannot get compiz working for the new users I created.

**System Overview**

[LIST]
[*]Ubuntu 7.04
[*]ATI Radeon X800 GTO
[*]ATI fglrx drivers (8.37.6)
[*]Compiz (XGL) + Heliodor
[/LIST]

**More on the problem:**
Compiz continues to work fine under my username. I am able to login to the other user's accounts fine with gnome, however when I try to login on an xgl session using one of the newly created users, X locks up (it freezes on a blank screen that is the color of the chosen background color for the system login). I Can shift+backspace to kill the x-session (goes to command line instead of login screen) at which point I normally have to force a restart before being able to get back to the xwindows login screen.

Alternatively, if I try running "xsession script" instead of Xgl for the session, it still locks up, but displays an error message as well, saying that the session lasted less than 10 seconds. If I then look at the output from .xsession-errors for the user, I find:

> 
.
.
.
Fatal Server Error
could not create server lock file: /tmp/.X1-lock
GTK-Warning**: cannot open display


I checked the file, and it's owner and group were both the original user. Thinking that perhaps it had to do with permissions for the file, I tried first backing up and deleting the file, and then chown'ing it to be owned by one of the newer users, but neither worked. I also tried changing my own account's group to match the group for the new users and then restarted X, but still no luck.

**Any ideas?**
So now I am stumped. &#40660;&#39522;&#25216;&#31406;...
Any help would be very much appreciated :)

Thanks!

---

### Post by nikogawa on 2007-06-03
see this thread

[http://ubuntuforums.org/showthread.php?t=323715](http://ubuntuforums.org/showthread.php?t=323715)

---

### Post by khughitt on 2007-06-03
That did the trick! Sorry I didn't pick that one up myself- I looked for variations of "multiple users," but did not catch that post.

Thanks :)

---

