---
title: "Remote desktop from SSH?"
date: 2012-10-25
forum: Desktop Environments
---

### Post by SlugSlug on 2012-10-25
Hi All,

We've changed a gfx card in a remote machine and on it's display (TV) it's 'not supported'

I have ssh access to the machine but if I ssh in and start vino-preferences then connect via vnc it loops back to my display :(


How do I get to remote view the machine? Or tinker with resolution settings I thought Xorg.conf was active in 10.04 but it doesn't seem to have any effect


Ubunut 10.04
Nvidia card with prop drivers now installed.


Many Thanks,

---

### Post by Lars Noodén on 2012-10-25
Have you tried reverse tunneling to the machine and then running the VNC server?  Then you'd connect to the forwarded port on the local host as usual for a tunnel.

---

### Post by SlugSlug on 2012-10-25
How do I do that?

ssh me@remote 
then 

then vino-preff &
then 
ssh -R 5900:me.com:9999

then vnc localhost 9999 ?

Its all very confusing :)

---

### Post by Lars Noodén on 2012-10-25
Sorry.  My mistake.  A normal tunnel would be needed.  

Tunnel to the remote, I don't have vino, but I expect that it is similar to x11vnc.  Start your VNC server on your remote machine, then connect to 5900 on your local host using the VNC client.  

```

ssh -L 5900:me.com:5900 "x11vnc -safer -localhost -nopw -once -display :0"

```

On my setup, I was not able to get VNC to accept a connection with a tunnel 9999:5900, it had to be 5900 on both ends.  Unmatched ports worked with other protocols, like SSH, but just not with VNC.

---

### Post by SlugSlug on 2012-10-25
Thanks 

I'll try tonight with that + x11vnc

---

