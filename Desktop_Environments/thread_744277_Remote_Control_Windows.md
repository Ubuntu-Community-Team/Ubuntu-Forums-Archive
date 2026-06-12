---
title: "Remote Control Windows?"
date: 2008-04-03
forum: Desktop Environments
---

### Post by smear3 on 2008-04-03
I am using Gutsy and would like to remote control the windows machines/servers in my environment.  I am not talking about RDP.  I need an application like Dameware or NetOp that takes control of the machine like you are sitting in front of it.  If anyone knows of or has used something like this it would be a big help.  I tried running Dameware in Wine but that seems to be a dead end.  Right now I'm using Dameware in a VMware session but I'd like to be able to use something straight from Linux.  Any help is appreciated.

---

### Post by diggity on 2008-04-03
I'm not sure what all NetOp and Dameware do, but I use VNC. I have Tight VNC Server on the Windows machines and connect from linux using xtightvncviewer.

hth.

---

### Post by smear3 on 2008-04-03
But that involves installing VNC on all the machines in my environment?  The cool thing about Dameware is that it installs the service when you try to connect to the machine.  Correct me if I'm wrong but with VNC you have to install the app on the remote machine manually before you can connect.  Or does VNC have an automatic type of install when trying to connect?

---

### Post by prshah on 2008-04-03
> **smear3 said:**
> But that involves installing VNC on all the machines in my environment?  Correct me if I'm wrong but with VNC you have to install the app on the remote machine manually before you can connect.  Or does VNC have an automatic type of install when trying to connect?

Yes you have to install it manually before you connect. Then you have to configure it. 

No automatic install.

---

### Post by smear3 on 2008-04-03
Yeah, that's a pain in the...for a large environment.  Maybe we can package it.   Otherwise I'm still up for recommendations.

---

### Post by eriqjaffe on 2008-04-03
Why isn't RDP an option?

Personally, anything that lets you connect to a PC without having a service previously installed on that PC seems like an **astonishingly** bad idea from a security point of view.

---

### Post by prshah on 2008-04-06
> **eriqjaffe said:**
> Why isn't RDP an option?

Personally, anything that lets you connect to a PC without having a service previously installed on that PC seems like an **astonishingly** bad idea from a security point of view.

+1; am I glad I'm not running Windows.

---

### Post by jlisek on 2008-04-17
How about trying [www.gotodevice.com](www.gotodevice.com), works nicely here:KS

---

### Post by timcredible on 2008-04-17
i have to agree with earlier poster - why is rdp not satisfactory?  i've never seen anything that can't be done via rdp.  make sure you connect as a console (with the /c parameter if you're doing it from command line) because there are a couple things you can't do with rdp unless you're connected as a console connection.

---

### Post by pepoluan on 2008-07-11
The TS almost echoed my need.

I need something like [**NetOp School**]("http://www.netop.com/netop-8.htm"), i.e. capability of totally taking over a computer, thus rendering my students unable to use their computer while I do some demo which I broadcasted to their desktops.

Is VNC able to do that? IIRC, VNC is 'voluntary' remote control, i.e., the person being controlled is able to terminate a VNC remote control session. CMIIW.

---

### Post by Stroppymoppy on 2008-07-17
Actually the way I would do it would be to have VNC Enterprise or if you want the Free VNC solution try a very cheap package called VNCSCAN. Both of these allow you to remote install VNC provided you have admin permissions. Also VNC does allow you to disable the remote keyboard and mouse whilst you are connected.

[http://www.vncscan.com]("http://www.vncscan.com")
[http://www.realvnc.com]("http://www.realvnc.com")

Hope this helps

Stroppy

---

