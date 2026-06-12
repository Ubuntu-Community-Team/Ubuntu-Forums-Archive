---
title: "xfce + vnc4server using :0"
date: 2009-09-09
forum: Desktop Environments
---

### Post by jackydany on 2009-09-09
hello

i'm new here but not new in using linux/ubuntu. but also not a professional :D

here is my problem:

i'm using ubuntu server edition 8.04 LTS and installed xorg + xfce4 etc as gui. i need a gui but wanted a small and lightweight system.
this omputer is going to be a small homeserver.
for this reason, there will be no display connected.
i want to start X by using ssh.
if i start X using startx as local user on the maschine and start vnc4server, it starts a new instance. i can now connect via vnc but will only receive a promt/shell.

what i want:
start X locally and use the existing X-session as VNC forward for maintenance.

so just use vnc4server :0 instead of :1 , the active X-session

is it possible by using vnc4server or have i to use vino ?

thanks a lot

stefan

---

