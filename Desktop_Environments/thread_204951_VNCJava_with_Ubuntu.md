---
title: "VNC/Java with Ubuntu"
date: 2006-06-27
forum: Desktop Environments
---

### Post by mykrob on 2006-06-27
Hey-
just did a new installation of Ubuntu on a system. I am able to hit it via vnc using vncviewer, but i need to be able to access it via a browser as well using port 5900.

When i try through a browser, i get a plain white screen with this message:

RFB 003.007

how can i enable Java-based VNC?

Thanks,
-myk

---

### Post by chrilleh on 2006-06-27
I have the same problem, only difference is that I get

RFB 003.008

---

### Post by kciampi319 on 2007-12-09
I get the same thing if i do port 5900 but according to the turorial I used but cannot find you shouldn't be using 5900.

My regular vnc server that uses vncviewer is based on port 5900, hower my java based server is based on 5800

so for example I have a startup script that runs vncserver -geometry 800x600 -depth 24 :3  This starts a vnc-java based server that is 800X600 on port 5803

so on my LAN you can type [http://ipofhost:5803](http://ipofhost:5803) to get the tidyvnc login screen.

also i would not really count on any security with this. (correct me if im wrong)  I keep mine accessible on my LAN only. and keep port 5800-5900 blocked in my firewall.  I use a vpn server.  This allows outside access, and security

And as a note i have installed x11vnc  tightvnc vnc4config vnc4server I may have an extra one i don't need in there but I had to go through a few tutorials before i got anything working. hope i helped

---

