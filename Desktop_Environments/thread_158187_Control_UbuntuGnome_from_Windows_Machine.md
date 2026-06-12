---
title: "Control Ubuntu/Gnome from Windows Machine?"
date: 2006-04-10
forum: Desktop Environments
---

### Post by OneSeventeen on 2006-04-10
I use windows at work so I can troubleshoot microsoft products, and would like to pop open a window with my ubuntu screen on it.  VNC is a little slow, XDMCP+CygwinX is insanely slow (on startup anyway, but fairly smooth after the 5 minue startup time) and both seem a little insecure.

Is there an equivalent to SSH for the GUI?  Possibly using SSH to transmit the data for a remote connection?

I'd prefer my windows machine be doing the display work, and the linux box just sitting there... so more of a remote logon that a remote controlling...  (meaning I don't want to take up my whole network doing VNCish stuff)

On a side note, can I do this from linux to linux as well?  Can I use my Ubuntu laptop to remote into my Ubuntu server, and bring up a GUI?  (Or would I be required to install X11 on the server, which I'd rather not do)

---

### Post by kingmonkey on 2006-04-10
[http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html](http://www.faqs.org/docs/Linux-mini/Remote-X-Apps.html)

I found the above site helpful for remote GUI. In reference to your laptop/server question refer to chapter 9.

---

### Post by souki on 2006-04-10
nomachine (or freenx) are quite good with bandwidth usage

---

### Post by OneSeventeen on 2006-04-12
Thanks all, I've looked a little into freenx/nomachine but wasn't sure if there was an easy way to install under Ubuntu, not to mention everything from nomachine costs $$.

As for the linux howto's, thanks for the link!  I'll probably be using the documents there a lot, and hopefully it will have a solution for my 15 minute startup times (I timed it yesterday, roughly 17 minutes from the time I log on to the time I can use applications).

And FYI, if anyone tries to get XDMCP to work on ubuntu and only gets a blank brown screen, just let it sit for 15 or 20 minutes, and something will eventually come up!

---

### Post by theduke0 on 2006-04-12
To do this from linux to linux is pretty simple.  

On the server, you should enable the XDMCP in gdm (security tab, i believe).  To get there, system -> administration -> login screen setup

On the client, from the login screen select sessions.  Then run xdmcp chooser.  If both machines are on the same network, the machine with xdmcp running should show up.  If that doesn't work, try the IP address.  

Let me know how it turns out

---

### Post by drbobit on 2006-04-21
I tried Xdmcp on another machine on my home network using a live CD and it worked really well :) thanks
Trying to do from an Xbox running XUbuntu next, wish me luck!

---

