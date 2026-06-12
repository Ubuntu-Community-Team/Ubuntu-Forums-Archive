---
title: "Remote graphical login"
date: 2005-05-24
forum: Desktop Environments
---

### Post by ioliver on 2005-05-24
I have two Ubuntu machines, one my desktop, and one a server, which will be headless (no kdb, mouse, screen)

On the desktop, I can get a new login and then use Ctrl-Alt-F7 and Ctrl-Alt-F8 to switch between the two users/desktops.
I can use "ssh -X server" to get a terminal where I can use X applications.

How can I get a graphical login to my server but where the X server is on my desktop so I use its screen, kbd, mouse etc?

I can use VNC, but it's a bit slow and not very pretty. It also seems to require me to be already logged into the server.

Thanks

Ian

---

### Post by nocturn on 2005-05-24
I think FreeNX can help.  There are backports-extras for it from Jdong.

---

### Post by ioliver on 2005-05-24
I've found what is (for me) a nice way of doing this.

Install the xnest package on the headless machine. Set its desktop resolution to < that of my monitor (1024x768 versus 1280x1024)

Then make a launcher for this command -
ssh -X tera gdmflexiserver -n

This sets up a ssh connection to the headless server (I've already swapped keys so I can login without a password) and then launches a gnome session in a window. Login to this session, and you can access the desktop of the server at any time.

Ian

---

