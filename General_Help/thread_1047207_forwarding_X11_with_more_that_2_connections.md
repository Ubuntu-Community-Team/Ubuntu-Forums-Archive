---
title: "forwarding X11 with more that 2 connections"
date: 2009-01-22
forum: General Help
---

### Post by therblack on 2009-01-22
Hi all,

I'm having problems forwarding more than two X11 connections.

If I do the following:

a) open a terminal, type "ssh -X host_name xterm"...I get a xterm
b) open a terminal, type "ssh -X host_name xterm"...I get a xterm
c) open a terminal, type "ssh -X host_name xterm"...I get the following error:

X11 connection rejected because of wrong authentication.
X connection to localhost:13.0 broken (explicit kill or server shutdown).

d)  open a terminal, type "ssh -X host_name xterm"...I get a xterm


Any ideas?  Does anyone else see the same error on the third login?

thanks

---

### Post by Dr Small on 2009-01-22
Are you connecting to the same host every time? and if so, why? You can either use 'screen' to open multiple screens and run the X11 applications you need, each inside a different screen, or you can try sending the process to the background with &

---

### Post by therblack on 2009-01-22
It doesn't matter whether it is the same host or not...a similar problem comes up with different hosts.

Incidently, this seemed to start happening with Intrepid.

thanks for you help

---

