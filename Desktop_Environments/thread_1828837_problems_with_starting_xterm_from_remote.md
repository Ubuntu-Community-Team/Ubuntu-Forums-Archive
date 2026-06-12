---
title: "problems with starting xterm from remote"
date: 2011-08-19
forum: Desktop Environments
---

### Post by BigLager on 2011-08-19
I am running hummingbird exceed on Workstation with an ip address of a.b.c.d, and connecting to a sun machine with IP address x.y.z.w running Solaris with XDMCP.  From the sun machine, we commonly telnet to other sun and linux machines and run X applications.

We have just installed ubuntu 10.04, and I can telnet into that machine no problem.

However, running xterm on the ubuntu machine fails:

xterm Xt error: cannot open display a.b.c.d:0.0

Can someone please point me in the right direction?

thanks!

---

### Post by collisionystm on 2011-08-19
You are using an xterm program on the ubuntu machine, or using xterm and connecting to ubuntu

---

### Post by BigLager on 2011-08-22
The xterm is being run on ubuntu.

I got it working by doing:

ssh -X user@host 

from the xterm on Solaris.

echo $DISPLAY on the ubuntu ssh session shows "localhost:10.0", not a.b.c.d:0

and xterm works -- but the font is unreadably small.  I can change this to HUGE, but it would be better to set a configuration parameter somewhere....

Also, xemacs is working from that ssh session.

Thanks!

---

