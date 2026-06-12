---
title: "Remote desktop using SSH"
date: 2007-10-23
forum: Desktop Environments
---

### Post by lastexyle on 2007-10-23
I'm trying to run a desktop session on a remote box (it's using some version of Solaris, but that's irrelevant as the trouble I'm having is on my end), but I'm having trouble figuring out how to give it it's own X session.

Here's my problem

I can log in and run single applications fine, but I'm running into trouble with a full desktop. just running gnome-session doesn't work since that means I have 2 full desktops on top of each other (my local gnome-session and the remote one on one display, obviously that's just a tiny bit cluttered).

I've figured out a way that sort of works, from the console, I can run "X :1 | xterm -display :1" This will launch a new empty X session with a terminal and I can then log into ssh (ssh -Y -l username ssh.server.example.com) and then execute gnome-session.

This sort of works, but it's rather cumbersome to do and if I close the xterm, the whole thing goes kaput. Ideally I'd like a script that I could just doubleclick on from within my local X session that'd start a new x session, log in to the remote machine, and run gnome-session. Does anyone know how to do this?

Thanks.

---

