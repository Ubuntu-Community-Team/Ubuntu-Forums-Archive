---
title: "Help! Remote desktop from Ubuntu to Vista that is attached to a router"
date: 2008-04-28
forum: Desktop Environments
---

### Post by edwin_cheung88 on 2008-04-28
Hey there!

I'm trying to Remote Desktop onto my work computer from my ubuntu. The work computer is on a router and running vista. I'm not having much luck using the Terminal Server Client provided by ubuntu. Is there a easier way for me to get on the vista?

---

### Post by kennethmsmith on 2008-04-28
you might need to explain what you have tried to do, and what type of error or response you are getting.  Do you know the IP address of the router and is the router configured to forward VNC or such type activity to the work computer that sits behind it?

---

### Post by b3y0nd on 2008-04-29
You will need to know the external IP of the Vista machine, configure the router to allow connection on the necessary ports, as well as the firewall "if any" on the Vista box. Then you will need to set up a remote desktop user on the Vista computer, or at least make sure your username is listed as a remote desktop user....with an enabled password on the account. 


From there you should* be able to connect, if not start from square one and check your firewall & router settings. 

Windows uses port 3386 for remote desktop. This port must be reachable from the external network. If you have nmap installed on Ubuntu or "similar" you can scan that port to verify it is open to the internet. You can also go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/).  Enter port 3389 and enter. 

If vista/router is configured correctly you will get a "Success" message.

Hope this helps

---

