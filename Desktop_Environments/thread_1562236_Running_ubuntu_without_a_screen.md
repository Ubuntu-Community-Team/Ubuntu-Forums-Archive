---
title: "Running ubuntu without a screen"
date: 2010-08-27
forum: Desktop Environments
---

### Post by palves on 2010-08-27
Hi,

I am trying to install a second ubuntu machine as a fileserver, which will be accessible from the network as an external drive and also via VNC. Everything went ok untill I put the machine in its final location and without keyboard, mouse or screen.

to my surprise I cannot access the machine (with VNC) without a screen because it gets stuck in a lowgraphics menu... 

i tried [http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx](http://stevenharman.net/blog/archive/2008/12/13/vnc-to-a-headless-ubuntu-box.aspx) but always get stuck in the same menu...

Any suggestion on how to fix this? I have look on the web and some people mention to comment out the line that reads:
 FailsafeXServer=/etc/gdm/failsafeXServer
In /etc/gdm/gdm.conf

but this file does not exist on my machine.

Any help?

thanks in advance

---

