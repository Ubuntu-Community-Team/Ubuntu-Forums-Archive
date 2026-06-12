---
title: "I want a xubuntu Desktop not a xfce4"
date: 2011-02-23
forum: Desktop Environments
---

### Post by forumi0721 on 2011-02-23
Hi...

I installed ubuntu 10.10 Server and install xubuntu-desktop use tasksel.

and I want to connect my ubuntu 10.10 Sever by VNC Server (RealVNC 4.6.0 x64)

but when I connect my desktop, it connect xfce4 session not a xubuntu-session..

What can I run xubuntu-session on my vnc connect?

please tell me xubuntu-session start command like  "gnome-session" for gnome or xfdesktop/startxfce4 for xfce4...

---

### Post by x1a4 on 2011-02-23
The main difference between Ubuntu and Xubuntu is that Xubuntu uses XFCE as its default GUI instead of GNOME.  So, in Ubuntu you start gnome-session.  In Xubuntu you start xfce4-session.  xubuntu-desktop is a meta package which installs XFCE and GTK applications and themes chosen for that flavour of *buntu.  Your "problem" is not a mistake, it's by design.

---

