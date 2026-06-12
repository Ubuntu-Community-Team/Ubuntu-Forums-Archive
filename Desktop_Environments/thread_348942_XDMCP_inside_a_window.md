---
title: "XDMCP inside a window"
date: 2007-01-29
forum: Desktop Environments
---

### Post by oayfer on 2007-01-29
I am running Ubuntu in a networked environment with lots of other UNIX systems (mostly Solaris and Linux). At times it is useful to work on a remote graphical environment.

I can do a "switch user" and use "Remote login via XDMCP" to get a login screen from one of the remote hosts. Then Ctrl-Alt-F7(8,9) works for going between the desktops.

I am wondering if anyone knows of a way to do this in a windowed way, without leaving my local Ubuntu desktop at all, a la VNC, without making any changes to the remote XDM settings.

Thanks.

---

### Post by bve on 2007-03-08
Sorry I can't answer your question, but thanks for the tip on using 'switch user' to open multiple x sessions on multiple machines.

I see XDMCP listed as a connection type in the Terminal Server Client, however in mine it is greyed out, which is why I stumbled in here.

In fact I prefer this over using a windowed connection, which as indicated above was what I was looking for when I found your post.


Again Thanks.

---

### Post by MoHaX on 2007-03-09
> **oayfer said:**
> I am running Ubuntu in a networked environment with lots of other UNIX systems (mostly Solaris and Linux). At times it is useful to work on a remote graphical environment.

I can do a "switch user" and use "Remote login via XDMCP" to get a login screen from one of the remote hosts. Then Ctrl-Alt-F7(8,9) works for going between the desktops.

I am wondering if anyone knows of a way to do this in a windowed way, without leaving my local Ubuntu desktop at all, a la VNC, without making any changes to the remote XDM settings.

Thanks.

I'm not familiar with ubuntu, but in general you shoul run "Xnest --ac -query servername:1". Xnest is a client for your Xserver (so it is rendered in window like any other program) and Xserver for remote host, so it could render remote  windows insite it's window. I suppose that this is what you are looking for.

---

### Post by geirha on 2007-03-09
yes, if you install the xnest package, you can use the Terminal Server Client in Applications -> Internet to connect with XDMCP

---

### Post by cahumphrey on 2007-03-21
geirha - thx for the tip, installing xnest worked perfectly, now I can xdmcp to my server in a small window and I don't have to log out and log back into my workstation session. :)

---

### Post by satbunny on 2007-03-30
This works well.
I can login to my remote Linux box and start a new session.
However using realvnc on my XP box I can connect and see my previously logged in session on the remote box, which I want to see to tweak settings, start and stop programmes etc.
How do I achieve this?
(I have tried vncviewer but it crashes reporting no useable font)
Can this be done using XDMCP? I can't see anything in the man pages for Xnest.

---

