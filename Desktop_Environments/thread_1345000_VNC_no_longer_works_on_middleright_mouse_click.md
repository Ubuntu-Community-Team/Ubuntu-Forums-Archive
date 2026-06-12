---
title: "VNC no longer works on middle/right mouse click"
date: 2009-12-03
forum: Desktop Environments
---

### Post by JohnSka7 on 2009-12-03
Hey all,

Having a really strange problem. I just finished setting up 9.10 server in a virtual machine at home and I have it set up for SSH and VNC.

The strange thing that is happening is when I'm VNCed on to the desktop (seems to be independent of program, I used Ultra, OSX Screen Sharing, etc) if I middle mouse click or right click, VNC crashes. I have tried this with and without the tightvnc server installed.

If I go into the Remote Desktop settings, it will usually allow me to log back in (VNC service restarts?) but it's not a guaranteed fix.

Anyone have any idea as to why this is happening?

---

### Post by Baked- on 2009-12-03
Im not sure what may be causing your problem, but after having many issues with VNC i found this [http://freenx.berlios.de/](http://freenx.berlios.de/) and i can tell you that it is way better than VNC, you should try it out.  (Also i had bad luck with nomachine's client so i am using qtnx and it seems to work well.)

---

### Post by toreador on 2009-12-10
For whatever it's worth, you're not alone. I'm having the same issue with right mouse clicks. Anytime I use my right mouse button, the VNC server crashes (have to go into Remote Desktop settings and un-check then re-check "allow remote connections" to get it restarted).

But I only experience this when I'm running virtually (latest VirtualBox- Ubuntu 9.10 client, running on 32 bit Vista host). When I dual boot into the version of 9.10 that resides on my physical machine all is fine.

It's strange alright.

---

