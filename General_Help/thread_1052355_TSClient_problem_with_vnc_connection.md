---
title: "TSClient problem with vnc connection"
date: 2009-01-27
forum: General Help
---

### Post by scottinsaskatoon on 2009-01-27
I have a vnc server running at home that I can connect to by putting the address and port into firefox, in the form of 
[http://xxxx.homeip.net:5800](http://xxxx.homeip.net:5800)   

A JAVA application then provides a connection.

I Want to use tsclient for this, but am not having any luck so far.  I have installed the xtightvncviewer and so have VNC as a protocol option, but when I put  xxx.homeip.net:5800 into tsclient and VNC as Protocol, and hit connect the tsclient window dissappears and nothing else happens.

However, I see that a process is now in system monitor called vncviewer.  If I kill that process, tsclient comes back up.

I get the impression that if I just knew how to view that process I would see my connection to my home computer.  Can anyone help me?  Thanks

---

### Post by scottinsaskatoon on 2009-01-28
For what its worth, I solved my own problem.

The server I have running at home uses two ports.  Port 5800 is set up to provide the java access, port 5900 is for non-java.  If I use 5900, then the vncviewer process works fine.

---

### Post by jonobr on 2009-01-28
Recommend you mark this as solved to assist others searching on similar problems

---

