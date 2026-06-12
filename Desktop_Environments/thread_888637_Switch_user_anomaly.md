---
title: "Switch user anomaly?"
date: 2008-08-13
forum: Desktop Environments
---

### Post by meburke on 2008-08-13
I have enabled root login on my private workstation (administrative needs). However, the screen saver does not lock the session, so I did a "switch user". When I switch from the root desktop to the other user, I get a message telling me that I have a session running and asking me if I want to resume it. However, when I switch user and log in as root, it spawns another session on a different tty port.

(For those of you who want to reproduce the problem: Pressing CTL-ALT F6, F5, F4, F3, F2 or F1 from the Window manager opens a shell login on another terminal port. From any of those shells, logging in is not necessary, ALT-F7 will take you back to the Gnome desktop. Apparently, the other user is spawned on the F9 port. F8 takes me to a port that seems to be stuck spawning something, and F10 had the second root desktop, but when I closed it it hung.)

This seems different from my previous experience with UNIX. If I wanted to use the alternate terminals, I would have logged in on them instead of switching users. What I really want, if anyone knows how, is to configure my system so that the screen saver locks the root session.

Thank you,

Mike

---

