---
title: "Freeze on X Server Restart"
date: 2009-01-29
forum: Desktop Environments
---

### Post by andqso on 2009-01-29
A strange problem: whenever I try to restart the X server, it refuses to appear and my computer eventually locks up with a black screen.

This is Intrepid, with xserver-xorg version 7.4.

I'm currently using KDM 4.2, but I experience the same problem in GDM (GDM is basically unusable because it restarts the X server whenever a user logs out, so I'm only allowed 1 login before the computer crashes). The issue occurs with Ctrl-Alt-Backspace, /etc/init.d/kdm restart, and /etc/init.d/kdm stop -> /etc/init.d/kdm start.

I have a nVidia Quadro NVS 140M, and I'm using the latest nVidia proprietary drivers.

Any idea what's going wrong here? Thanks for your help.

---

### Post by andqso on 2009-01-30
To clarify, that's with GDM 2.20.8.

---

