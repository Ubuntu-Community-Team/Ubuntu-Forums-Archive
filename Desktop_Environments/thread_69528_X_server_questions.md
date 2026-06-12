---
title: "X server questions"
date: 2005-09-27
forum: Desktop Environments
---

### Post by richardqr on 2005-09-27
Hi,

I have used Linux but I really don't know how to "play" around with it.  Can you help me with the following:

1. how do I exit from X (terminate the X server)?  how to I load it up again>
2. If I log in a GNOME desktop, how do I connect to other servers via XDMCP.  My goal is to log in to my local desktop and also allow me to remotely connect to a remote X machine.  In windows, it is easy by using Cygwin/X, Hummingbird, or X-Deep.  What is the Linux equivalent for these?  
3. If there is none, how do I switch my X server to host the remote client instead of my local machine.  Or, how do I "share" my X server into two X sessions (one local, one remote X client).

Thank you in advance.

-richard

---

### Post by bob k on 2005-09-27
[QUOTE=richardqr]Hi,

I have used Linux but I really don't know how to "play" around with it.  Can you help me with the following:

1. how do I exit from X (terminate the X server)?  how to I load it up again>
2. If I log in a GNOME desktop, how do I connect to other servers via XDMCP.  My goal is to log in to my local desktop and also allow me to remotely connect to a remote X machine.  In windows, it is easy by using Cygwin/X, Hummingbird, or X-Deep.  What is the Linux equivalent for these?  
3. If there is none, how do I switch my X server to host the remote client instead of my local machine.  Or, how do I "share" my X server into two X sessions (one local, one remote X client).

Thank you in advance.

-richard[/QUOTE]

I can answer number 1.
to exit X enter ctrl alt backspace  (just like a win reboot).

This will put in command mode, and at this point you can use the basic linux commands (cd, rm,mkdir....)

when done enter startx & password to restart X.

For 2 & 3 I would look at samba or a VPN app,  just for security.

---

