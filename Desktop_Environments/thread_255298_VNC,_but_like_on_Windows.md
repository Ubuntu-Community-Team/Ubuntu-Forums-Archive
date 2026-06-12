---
title: "VNC, but like on Windows"
date: 2006-09-11
forum: Desktop Environments
---

### Post by apanloco on 2006-09-11
I have set up VNC on my MythTV machine, with the help of some howtos on this forum (thanks all). It works, but it's not really what I want.

The problem is that the VNC session is separate from the X-session on the computer. I want to be able to log in, and control my MythTV box, as seen on the TV. I want to log in on the X-session and see the same thing on my TV (tv-out) and my VNC client. Just like it works on Windows. How can I do this?

BR/D

---

### Post by apanloco on 2006-09-12
The answer is to use x11vnc. This vnc server, in contrast to "regular" vnc server (tightvnc, ultravnc, realvnc...), attaches to the local x display. Hope this helps someone!

---

