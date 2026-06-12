---
title: "Remote Display"
date: 2007-06-17
forum: Desktop Environments
---

### Post by jdpellegrino on 2007-06-17
First I am not certain if this is the right forum if not let me know. ;)

OK, so I just recently installed Ubuntu and I seem to be having difficulty opening remote X connections.
Example: 

Laptop1 with Ubuntu - xhost + (Access enabled from any....); ssh -X laptop2
Laptop2 (Fedora Core 4): setenv DISPLAY laptop1IP:0.0; xv

xv: Can't open display

The sshd.config in Laptop2 has X11Forwarding set to yes and I don't see anything useful in the logs.

Any thoughts? Thanks.

---

