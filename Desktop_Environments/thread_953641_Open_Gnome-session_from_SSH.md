---
title: "Open Gnome-session from SSH"
date: 2008-10-20
forum: Desktop Environments
---

### Post by pmgallardo on 2008-10-20
We're using Ubuntu LAMP Server inside a LAN, just for testing, for people who are completely new to Linux. Because of this, they had told me to install the IDE as well.

I need to access the server remotely, so I have installed Tight VNC Server and I can connect the server using a VNC Server. The problem is that the GNOME session is not loaded, and I have to get to do it.

If I type "gnome-session" from the VNC viewer, everything we'll be loaded correctly, but the main problem is that the user is root and I want to avoid it if it's possible.

I tried to make "su username" and then "gnome-session" but I get this message:

Gtk-WARNING **: cannot open display

I have looked other topics but I couldn't find anything that worked. Any ideas about how to solve this problem? Thanks in advanced!

---

