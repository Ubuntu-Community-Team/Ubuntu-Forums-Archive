---
title: "Vnc connection refused"
date: 2005-10-07
forum: Desktop Environments
---

### Post by iitywygms on 2005-10-07
Hey everyone
I have been using ubuntu for about a year now and love it.  I am getting the hang of linux but I have a lot to learn.  I even got my laptop to work with ndiswrapper, after about a months reading.  I am stuck on this one thing.  
I am trying to get vnc to work on my desktop machine.  I have followed this guide [http://www.ubuntuforums.org/showthread.php?t=42941&highlight=vnc+connection](http://www.ubuntuforums.org/showthread.php?t=42941&highlight=vnc+connection)
but still no luck.  Everytime I try to connect to this computer from either my linux laptop or my windows machine, I get connection refused.  I think it has to do with either my firewall on linux, or the way vnc is configured.  I have disabled the firewall on my windows machine and still no luck.  Am I missing something easy?
Thanks for the help

---

### Post by KingBahamut on 2005-10-07
Try running vncserver from the command line. 



if you want an active connection to an active desktop , try x11vnc.

---

### Post by cstudent on 2005-10-07
If you are running Firestarter on your Linux machine you will have to set it up to allow the connection.

---

### Post by iitywygms on 2005-10-07
Thanx for the quick reply.  I am not runnig firestarter.  I believe I have already install x11vnc but not sure if I used it correctly.  I have tried running vnc from the command line and still get same result, connection refused.  Is there a certain setup procedure I need to do first?
What I am trying to do is set my machine up as a headless unit.  I want to use it as a server but need to be able to connect to it from a differnt computer.  If there is something else out there that works like winblows remote desktop, maybe I should try that.

---

### Post by iitywygms on 2005-10-07
Um,](*,)  thanx for the help.  A quick tip for people trying to do this, use the correct ip address. DOH

---

