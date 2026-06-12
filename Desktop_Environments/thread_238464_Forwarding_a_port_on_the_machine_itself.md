---
title: "Forwarding a port on the machine itself"
date: 2006-08-17
forum: Desktop Environments
---

### Post by grav on 2006-08-17
I'm using the built-in "Remote Desktop" feature of Ubuntu on my home machine, which is actually a VNC-server. It runs on port 5900 and as far as I can understand, it is currently not possible to change this.

However, I'm often connecting to my Ubuntu machine at home from behind a firewall which only allows traffic on certain outgoing ports, none of them being 5900.

Since my router at home does not allow me to forward incomming traffic from port x to y, I was wondering if Linux allows this. 

That is, can I set up my Ubuntu machine to change all traffic coming in on eg. port 3389 to port 5900, thus forwarding it to the VNC server running on the machine?

Regards, Mikkel

---

### Post by arkham on 2006-08-17
Hi Mikkel - I had a similar problem with web traffic, and used squid running on a non-firewalled machine to get around it.  Since ssh is allowed in most places, from the non-firewalled machine running squid I did the following:

ssh -N -f -q -R 8080:localhost:3128 [email]username@firewalled.machine.com[/email]

This essentially uses ssh to tunnel the traffic and reroutes local port 8080 on the firewalled machine to port 3128 (squid) on the non-firewalled machine.

If the machine you are connecting from is running windows - google for how to do similar stuff on Putty.  I think yours would look something like this:

ssh -N -f -q -R 5901:localhost:5900 [email]username@firewalled.machine.com[/email]

Then you point your VNC client at localhost:5901 and you should be good to go......

---

