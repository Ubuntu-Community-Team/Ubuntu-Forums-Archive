---
title: "Which Ubuntu 7 -&gt; Ubuntu 7 Remote Desktop tool (with these specific reqs)?"
date: 2007-06-02
forum: Desktop Environments
---

### Post by jtkirk on 2007-06-02
I would like some guidance about WHICH product I should be looking at to accomplish this specific function:

I have Ubuntu 7.04 at HOME (fully operational)
I have Ubuntu 7.04 at WORK (fully operational within the networked environment). 

I want to be at HOME and connect (AND login!) to my WORK computer for the sole purpose of acting as if I'm at work while still at home.

Side Note: I do *not* want to share disk drives, copy files, connect the reverse scenario or otherwise connect my home and work computers.     (many posts mix these requirements and i get confused)

So, before I learn the technical "how to" details, does anyone know what product is best suited for this specific task?
vncviewer?
TightVNC
vino?
Other?

vino does not seem to be the right choice since my work computer may not be logged in when I'm trying to connect.

I appreciate any help.

---

### Post by Xappe on 2007-06-02
I would try freeNX. It's a remote desktop server/client suite that works over a secure ssh connection. It's a really fast one too. 

One disadvantage from normal VNC though, is that if you wan't to suspend your desktop from home, and go to work to continue from there, you have to use the NX client locallly on the work machine to connect to the suspended NX desktop.

---

### Post by jtkirk on 2007-06-02
Thanks for the advice.  I'll read more about it.

Why would someone choose freeNX over VNC, in your opinion?    And when you say 'normal vnc', so you mean vncviewer or 'tightvnc' (I'm not sure about the difference)

---

### Post by Xappe on 2007-06-02
As far as I know a VNC server lets you connect to a running session on the server machine, that is...what you see on your client is the same thing that you could see on the server machine. 

NX uses some form of x-forwarding, that is, all the X calls are forwarded to the remote computer over the network without being processed graphically at all at the server box (someone correct me if i'm wrong). Therefore a NX session cannot be the same as a local session logged in from gdm (for example).

Hope i'm not too far off here :)

Read more on the nomachine pages:

[http://www.nomachine.com]("http://www.nomachine.com")

---

