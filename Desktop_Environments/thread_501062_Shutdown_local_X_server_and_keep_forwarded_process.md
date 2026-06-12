---
title: "Shutdown local X server and keep forwarded processes running?"
date: 2007-07-14
forum: Desktop Environments
---

### Post by chadjohnson on 2007-07-14
Hi, I have two Ubuntu machines -- laptop and server -- and I can start a remote gnome session and forward it to a local X server with the following commands at a tty console:

X :1 vt8 &
export DISPLAY=:1
ssh -X -C user@remotehost
gnome-session &

So that's great -- I can separate my development desktop from my personal desktop -- but the problem is, when I shut down the local X server, the remote gnome session goes down with it. Is there any way to keep the remote gnome session up and running on the remote machine whilst shutting down the local X server? I want to be able to, if needed, turn on my local computer and then resume the session later (without using VNC or XDMCP).

And if this is possible, might anyone know how to resume the gnome session?

Could I somehow do this with nohup or screen?

---

### Post by chadjohnson on 2007-07-16
bump...anyone?

---

