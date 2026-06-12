---
title: "how to setup VNC to access local display instead of a login to GDM!?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by syntek on 2006-07-27
ive been using VNC for awhile on Ubuntu (currently 6.06 up-to-date) and I have it configured so it spawns a new session and I am brought to a GDM login screen. How can I configure VNC so that I can view and/or control the same GNOME desktop as if I was sitting at the machine??

For instance, lets say I'm working on something but would like to go into the living room and do some other work on my laptop, then fire up vncviewer and check the progress of where I left off.

I haven't been able to find a HOWTO on getting VNC to work with the local session. If I fire up VNCviewer now, and connect to my ubuntu desktop, I'm brought to a GDM login where I can login and start a new session.

Additionally, Is it possible to have VNCserver spawn 2 servers, so I can connect to either the remote machine's "local display", or start a new session through GDM by changing the port #?

Thanks a ton in advance, I'd really love to get this going! Any help or pointers would be greatly appreaciated.

---

### Post by simplyw00x on 2006-07-27
GNOME has a VNC server for the current session built-in, called vino:

System / Preferences / Remote Desktop

---

### Post by halitus87 on 2006-11-01
ok im glad i think i can finaly help with something

i had a simmilar but opposite problem

i could only logon to the current session and couldnt start a new one if  or even connect if it wasnt already loged in

u should be able to access the first session (assuming its already loged in )
by using the code

 vncviewer -fullscreen <<<ip>>>:0

the :0 is the first session

im assuming your using <<<ip>>>:1 which should open a new session

hope it helps

---

