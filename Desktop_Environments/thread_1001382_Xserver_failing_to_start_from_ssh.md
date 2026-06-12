---
title: "Xserver failing to start from ssh"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Pits0r on 2008-12-03
Hey guys,

8.10 server install, installed the gnome gui to make it more friendly for less knowledgeable people (myself inccluded) to maintain the system.

SSH works, GUI locally works, but sshing in and running sudo startx is failing with this error:

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit:  Interrupted system call (errno 4):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

Any subsequent attempts I get this:

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

xinit:  Server error.


I suspect it has something to do with the restricted driver I installed for the graphics card, rebooted and borked itself.

Any ideas guys?

---

### Post by sirjoebob on 2008-12-03
I don't know that you can run the entire xserver remotely. I know you can use X11 forwarding to run graphical apps remotely. This is probably a better option anyways.

If you don't know how to use x11 forwarding, look it up on google, there are good tutorials but i think you use "ssh user@host -x"

I have done it before and it runs pretty good.

---

