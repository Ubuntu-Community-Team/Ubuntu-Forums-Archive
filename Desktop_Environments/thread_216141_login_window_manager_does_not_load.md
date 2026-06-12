---
title: "login window manager does not load"
date: 2006-07-15
forum: Desktop Environments
---

### Post by digitalcat12 on 2006-07-15
I installed KDE desktop on Ubuntu, and now I can't launch the "login window" from the system/adminstration menu under Gnome. When I click on it and the hour glass just runs, then nothing. Any ideas?

---

### Post by aysiu on 2006-07-15
What do you mean by the *login window*...?

Do you mean this?

If so, try running the command ```
gdmflexiserver
``` from the command line.

---

### Post by Jason.TJ.Johnson on 2006-11-17
I'm having the same problem but on top of that I'm having another problem.

When I start the computer the x server doesn't load it. It simply sits at a prompt asking me to login. I have to manually login and type "startx" to get the window manager to show up... This happened, I believe, right after installing KDE.. Anyway, I tried running the command you mentioned and here's what I get..

[quote=Jason's terminal]
jason@jason-desktop:~$ gdmflexiserver
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
[/quote]

Also, on a side note, logging out also takes me back to the prompt...

Help please! I've been researching and I don't know what to do.

---

### Post by stucky on 2006-11-18
Same here.

---

