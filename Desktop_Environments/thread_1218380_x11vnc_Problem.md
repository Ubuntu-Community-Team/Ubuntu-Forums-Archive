---
title: "x11vnc Problem"
date: 2009-07-20
forum: Desktop Environments
---

### Post by l2e on 2009-07-20
After a 10+ year hiatus from linux, I am diving in head first and replacing all my Vista HTPC's with a minimal install of ubuntu and XBMC starting up with x. So I followed this HOW-To to the letter:
 
[http://xbmc.org/forum/showthread.php?t=53812](http://xbmc.org/forum/showthread.php?t=53812)
 
and I have a fully functional XBMC set top box. However, now I want to be able to do other things. For one, I want to be able to VNC to my HTPC from XP laptop. I installed x11vnc and ran this command from a putty terminal:
 
x11vnc -nopw -accept -once -viewonly -display :0
 
I then run vncviewer from my laptop and I see the following in the putty terminal:
 
20/07/2009 13:09:37 accept_client: rejected: 192.168.1.250
20/07/2009 13:09:37 denying client: 192.168.1.250 local user rejected connection 
 
and vncviewer comes back with connection rejected.
 
What am I doing wrong?

---

### Post by krunge on 2009-07-20
> 
x11vnc -nopw -accept -once -viewonly -display :0
 
I then run vncviewer from my laptop and I see the following in the putty terminal:
 
20/07/2009 13:09:37 accept_client: rejected: 192.168.1.250
20/07/2009 13:09:37 denying client: 192.168.1.250 local user rejected connection 
 
What am I doing wrong?

You are not using the "-accept" option correctly.

I suggest dropping it from your command line (or learn how to use it here: [http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-accept](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-accept))

---

