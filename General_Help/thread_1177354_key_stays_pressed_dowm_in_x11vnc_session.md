---
title: "key stays pressed dowm in x11vnc session"
date: 2009-06-03
forum: General Help
---

### Post by bsautner on 2009-06-03
Hello - check this out. Clean Ubuntu 9.04 host runing vmware server. A clean install of same on a new guest virtal machine. I install open-ssh on guest and x11vnc

From an xp pc on another network i use putty to open a ssh session into guest and which also sets up a tunnel to the xllvnc server port on the guest.

i log into guest via putty and run (XXXX is port #)

 x11vnc -ncache -rfbport XXXX -rfbauth ~/.vnc/passwd  x1

which established the tunnel to XXXX

then use vncviewer on the xp client and connect to 127.0.0.1:XXXX

works great, i'm tunneling into my x11vnc session. 

i install eclipse 3.4

then - randomly throught the day, when i press the letter t when typing it stays pressed down. every text box with focus fills with the letter t. 

I installed vmware client tools - no luck

rebuilt new guest os from scratch went just installed x11vnc, ssh and got same behavior.

get this - if i end my sessions and go to the host and use a vmware console applet to view the host the letter t is still being pressed.  I'm not sure if eclipse, vmware or x11vnc is the problem - has anyone seen a key staying pressed during an x11vnc session?

---

### Post by krunge on 2009-06-03
See this thread: [http://ubuntuforums.org/showthread.php?t=1125694](http://ubuntuforums.org/showthread.php?t=1125694)

The workaround is the "-repeat" x11vnc option.

---

### Post by bsautner on 2009-06-05
Thanks, i was just logging in to share that i found that and can confirm it resolved the problem of repeating key

---

