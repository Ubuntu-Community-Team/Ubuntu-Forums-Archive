---
title: "Using VNC viewer from a remote machine"
date: 2008-04-21
forum: Desktop Environments
---

### Post by NCLI on 2008-04-21
So, I setup my PC to be accessible from any PC without my confirmation, just by entering a password. This works just fine from machines on my local network, but the command "vncviewer computername1:0" obviously doesn't work from a remote machine.

What should I add to the command to make it work?

Oh, and my PC is behind a router, with a static, router-assigned IP.

---

### Post by trippinnik on 2008-04-22
you'll need to know your outside IP address or have a domain name.  Then you'll need to setup port forwarding with your router, VNC usually default to port 5900, and forward it to the appropriate machine inside your local network.

---

