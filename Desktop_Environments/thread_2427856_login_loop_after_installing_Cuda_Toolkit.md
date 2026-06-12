---
title: "login loop after installing Cuda Toolkit"
date: 2019-09-26
forum: Desktop Environments
---

### Post by ken18 on 2019-09-26
I'm about ready to throw in the towel and re-install everything but figured I'd make a last ditch attempt first via this forum.  I have ubuntu 16.04 on a desktop computer.  Here is the sequence of events from yesterday.

1. Installed tightvnc (and xfce4) to have remote access via my laptop in another room of the house.  Everything worked great.  I could access the desktop terminal via Putty and the (xfce) desktop via tightvnc. This might not be relevant but i figured I'd provide a complete history.

2. I then installed CUDA so I could do some GPU programming and after adding PATH info in ~/.bashrc I've had trouble logging into the desktop.  I don't know why, but the login screen shows 4 desktop choices: GNOME (default), GNOME (classic), Ubuntu, and xfce.  I'm puzzled that so many choices show up.  Xfce makes sense because I installed it for tightvnc, but I don't know why the GNOME choices are there (my understanding is that ubuntu 16.04 uses Unity, not GNOME).  In any event, any choice except xfce brings me right back to the login screen.

3. I'm quite sure the problem is CUDA related.  For one, when I logged in via shell, my PATH variable was messed up because I couldn't use basic commands like sudo, ls, etc.  I figured I must have botched the modification to ~/.bashrc so after much fooling around I was able to comment out the additions I made for CUDA.  At least after that the terminal sessions worked ok but desktop still doesn't (except for xfce). Secondly, at some point I did see an error message that some component of CUDA didn't install properly.

4. I tried the standard things I could find for solving login loop (.Xauthority and \tmp permissions) and several others like uninstalling CUDA (which doesn't seem to be complete), reinstalling the desktop, and others that I can't now remember.

What puzzles me is (1) why I have so many desktop choices, (2) why none of the desktops work except for xfce and (3) what to do

Suggestions?

---

### Post by #&amp;thj^% on 2019-09-26
Some how, in your install you pulled all these in.
To be clear Unity is GNOME, Unity is just a shell wrapped around Gnome, as is the same for Gnome Shell.
Wayland could be in play here.
Also did you try adding "nomodeset" to "/etc/default/grub"?

---

