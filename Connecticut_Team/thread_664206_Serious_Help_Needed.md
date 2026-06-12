---
title: "Serious Help Needed"
date: 2008-01-10
forum: Connecticut Team
---

### Post by evilbuntu on 2008-01-10
I use tight VNC to remote into my server.

i started installing my samba then had to stop because i was doing it remotley and didnt have my disk in the server drive at home (where i wasnt)

i now get a hang up and "readexact: socket error while reading" message blocking me from remotely entering.

i have seen many posts but no solutions to this issue with others, is this an issue that requires a full re-install or is there a VNC repair function or would completley removing the VNC capability from Ubunu server 7.10 then reinstalling help?

someone please give me a route to take, i would rather figure out the problem in case it happens again instead of just erasing it till it happens again.

thanks in advance:(

i can still core into the server remotley just not VNC it.

---

### Post by stalker145 on 2008-01-11
> **evilbuntu said:**
> I use tight VNC to remote into my server.

i started installing my samba then had to stop because i was doing it remotley and didnt have my disk in the server drive at home (where i wasnt)

i now get a hang up and "readexact: socket error while reading" message blocking me from remotely entering.

i have seen many posts but no solutions to this issue with others, is this an issue that requires a full re-install or is there a VNC repair function or would completley removing the VNC capability from Ubunu server 7.10 then reinstalling help?

someone please give me a route to take, i would rather figure out the problem in case it happens again instead of just erasing it till it happens again.

thanks in advance:(

i can still core into the server remotley just not VNC it.

Have you tried rebooting the server yet? That may clear up the problem. If the problem persists after a reboot... I don't know, maybe a reinstall of the VNC software.

---

### Post by evilbuntu on 2008-01-11
> **stalker145 said:**
> Have you tried rebooting the server yet? That may clear up the problem. If the problem persists after a reboot... I don't know, maybe a reinstall of the VNC software.

reinstall of the tight VNC ot the linux installed vnc controller?

---

### Post by zipperback on 2008-01-11
When doing remote work on servers, I have found that it is best to stay away from things like vnc and other remote gui desktops, and just use ssh for remote management sessions.

- zipperback
:popcorn:

---

