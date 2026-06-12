---
title: "Starting VNC as a service"
date: 2005-07-15
forum: Desktop Environments
---

### Post by tonyvfield on 2005-07-15
Not being a wizard at all, I would like to start VNC as a service so that providing the PC is powered on I can log into it remotely and operate it. Perhaps this is not the correct method, so very open to suggestions.
The PC I want to operate powered up 24 x 7 but without keyboard, screen etc. Since I sometimes have power failures, I need whatever service to be running before anyone is logged in as there will be no keyboard etc conencted

Simple suggestions welcome  ;-) 

Regards

Tony

---

### Post by cwaldbieser on 2005-07-15
How about running an ssh server?  Clients are available for UNIX and Windows (via PuTTY), and it is still pretty responsive over slow connections as well as being secure.  If you need a graphical display, you can start up VNC on Ubuntu and have it forwarded back to your local PC.


This link explains the basics:
[http://www.uk.research.att.com/archive/vnc/sshvnc.html](http://www.uk.research.att.com/archive/vnc/sshvnc.html)

---

### Post by tonyvfield on 2005-07-15
Thanks, this looks wonderful, I will experiment over the weekend

Tony

---

