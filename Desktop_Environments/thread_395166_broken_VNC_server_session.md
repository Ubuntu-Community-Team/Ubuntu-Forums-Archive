---
title: "broken VNC server session"
date: 2007-03-27
forum: Desktop Environments
---

### Post by irish_flu on 2007-03-27
Hey folks-

I have a VNC session I can't get into, and the machine is far far away.

The story is this:  The other day I was at my office (800 miles from my house) and set up a server that had just been laying around.  The Win2k install on it was jacked, so instead of reinstalling that poor old OS in threw in my trusty Ubuntu Dapper CD.

I installed vnc4server and got it up and running using the info in this awesome thread:
[http://www.ubuntuforums.org/showthread.php?t=191564](http://www.ubuntuforums.org/showthread.php?t=191564)

So, I got home and began working with my server.  Because of my own idiocy, I realized just this afternoon that the local IP I gave the machine has a conflict.

So, I logged on to the VNC session and changed the IP on the box.  Lost the VNC session (of course), so I gave my TightVNC client the new IP address and tried to log in.

Problem is, I get "VNC Authentication failed" whenever I try to log back in to the session. :confused: 

I assume that the session is somehow tied to the old IP.  It's the only available VNC session on that box, unfortunately.

To make matters worse, I forgot to make it so I could telnet or ssh into the thing (OOPS, I was in a hurry; I was gonna set that up after I got the IP changed).

I have somebody I work with who lives nearby who's willing to go do a reboot on the thing.  My question is:

Will the reboot (since that should kill my VNC session) make it so that I can log in again, or is there something I'm missing here?

---

