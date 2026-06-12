---
title: "Need to remote into an XP station"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Master Shake on 2006-02-10
A friend across the country got a rootkit on his XP.  I want to connect in to take a look at it.  Is there a way to do this thru Ubuntu?

---

### Post by PapaWiskas on 2006-02-10
Use Terminal Services Client (should be in your Internet category on your menu system)....when I connect to my XP boxes here at work with my Ubuntu I have the connection type set to RDPv5
I have 12 servers 150 workstations all running either 2000 or XP Pro.

He just needs to make sure he has a user created on his box for this purposes of remote connecting, and that remote desktop is enabled.

---

### Post by ebash on 2006-02-10
If you are confortable with the command line take a look at the command rdesktop. I think that the 'Terminal Services Client' is a frontend to rdesktop or VNC depending on the protocol selected.

Using the command line version has some advantages like sharing your local disk with the remote server.

---

### Post by harisund on 2006-02-11
As informed above, VNC and Remote Desktop are perhaps the best ways (and the only ways too, I think.) that a remote Windows machine can be controlled. However, before either can be done, your friend must have done a couple of stuff on his machine. 

For VNC, your friend should install a VNC server. 
For Remote DEsktop, your friend should instruct XP to allow remote desktop. 

Either way, things get complicated if the friend either has a firewall installed, or instead of directly connecting to the internet is connecting through a wireless router or something.

---

