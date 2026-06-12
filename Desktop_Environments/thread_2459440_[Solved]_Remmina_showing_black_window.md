---
title: "[Solved] Remmina showing black window"
date: 2021-03-18
forum: Desktop Environments
---

### Post by Cadryc on 2021-03-18
I want to remote control one computer with Ubuntu 20.04 from another computer with Ubuntu 20.04 on the same network.

I enabled screen sharing in settings in the first computer (A)

I open Remmina on the other computer (B) and connects to A, choosing vnc. I get the password prompt (wich I chose on A) and get a window that is black inside. On A a notification says a remote user is connected.

I tried playing around with settings as quality to highest, various color depth but I only get the black window.

Suggestions?

EDIT I tried to open nautilus on A, while B is connected, and nothing happens. But on B nautilus opened inside the black window.

---

### Post by ActionParsnip on 2021-03-19
What are you wanting to do on the remote system once you connect via VNC? There may be a sleeker solution to what you want to achieve

---

### Post by Cadryc on 2021-03-19
An easy and convenient way to manage the computer, see what programs are running and manage them

---

### Post by Cadryc on 2021-03-19
I discovered that it worked if a display was connected to B, which led me to this solution with a dummy display

[https://askubuntu.com/questions/1033436/how-to-use-ubuntu-18-04-on-vnc-without-display-attached](https://askubuntu.com/questions/1033436/how-to-use-ubuntu-18-04-on-vnc-without-display-attached)

So problem solved, thou one thing from perfect is that I don't seem to be able to change to a higher resolution than 1360x768 on the dummy display, even thou I specified 1680x1050 in /etc/X11/xorg.conf

---

