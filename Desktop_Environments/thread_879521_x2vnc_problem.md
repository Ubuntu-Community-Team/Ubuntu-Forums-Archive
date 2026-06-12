---
title: "x2vnc problem"
date: 2008-08-04
forum: Desktop Environments
---

### Post by stuque on 2008-08-04
Hi,

Has anyone managed to get x2vnc workign with Hardy? I am trying to get x2vnc running on Hardy to connect it to Windows.

I have tightvnc working okay between the two computers.

When I run x2vnc I get this message:

$ x2vnc -west 192.168.1.X:0
x2vnc: VNC authentication succeeded
x2vnc: Desktop name "windowscomputer"
x2vnc: Connected to VNC server, using protocol version 3.3
x2vnc: VNC server default format:
screen[0] pos=1004
Xinerama detected, x2vnc will use screen 1.
x2vnc: pointer multiplier: 0.880112

When I move the mouse pointer to the west edge of the Ubuntu screen, the pointer disappears, but the Windows screen does not appear.

I guess it has something to do with Xinerama causing the screen to be switched to 1 instead of 0? I only have one monitor, and have never set up any multi-screen stuff.

---

### Post by mulad on 2008-11-07
Considering you posted this a while ago, hopefully you know the answer.  But since I hit this page after doing a Google query, I'll point out that x2vnc does not display the remote desktop -- it only moves the mouse pointer onto the remote screen when you get to the edge.  It is used when you have two computers with their displays physically located right next to each other.  It's a useful tool to prevent you from getting confused about which keyboard to use when you're sitting in front of multiple computers  -- instead, you just use one "primary" keyboard and mouse pair to control all of the systems.

---

