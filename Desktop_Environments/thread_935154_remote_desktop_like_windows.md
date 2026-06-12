---
title: "remote desktop like windows"
date: 2008-10-01
forum: Desktop Environments
---

### Post by tigerstripedcat on 2008-10-01
Hello you great ubunutu community,

I would like to find a way to remote into my work computer with the following requirements:

1) Remote into the currently running session (on work computer)
2) Lock the remote display so no one can see my work
3) Fast connection

Incidentally, RDP and Windows fulfill all these requirements perfectly on my windows machine that I run in parallel next to my Linux box.

What I've tried so far:

_Persistent Nomachine remote session_
Run a Nomachine session on my work computer locally, grab that session if I need to work on it remotely, and then reattach it at work when I need it again.  So basically I "remote" into the same machine I work on.
Pros:  Decent speed, "locks" screen because session is detached from work computer.
Cons: Inefficient use of CPU.  I have a noticeable speed decrease (but not from the network) when I don't have to, say, run a youtube video through NX which means about a 30%CPU usage with nxssh and 30%CPU usage with nxserver.  It's surprisingly usable, but it seems like a waste when I should be able to work like windows/RDP and just remote into the currently running session

_Nomachine "shadowing"
Nomachine as the ability to connect to the currently running session.
Pros: Less CPU usage
Cons: Can't lock the remote screen so what I do is visible, and the display looks HORRIBLE--I can barely read the fonts.

_VNC_
Cons: Way too slow, can't lock screen.

_2X_
Haven't tried it

_RDP_
I heard there's a revamping of KDE4's remote software to support this?  Let's hope it can get something as good as we have with the Microsoft Terminal Services/RDP

Right now I'm going to try running two sessions, a local and a remote with nomachine.  I'll shadow into the "local" session from home if I really need some info or can't afford to rerun a task (say a essential job is running on the "local" session), but even this seems like a tremendous waste of memory.

Anyone have any better setups?
Thanks!

TSC

---

### Post by Locke_99GS on 2008-10-01
Xephyr + SSH.

---

