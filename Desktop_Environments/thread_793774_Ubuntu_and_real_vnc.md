---
title: "Ubuntu and real vnc"
date: 2008-05-14
forum: Desktop Environments
---

### Post by rcor on 2008-05-14
Dear users of the ubuntu forums,

I've installed Real Vnc under Ubuntu, but I don't no how this program works. So I want to ask all readers of this thread of they now how I can get Real Vnc to work.

Thanks for all help.

---

### Post by KingWilliam on 2008-05-14
What are yo trying to do? Access a remote machine? Or access the system you are working on from an other location? 

VNC works with a client server. You should install the server on the machine you want to access and the client on the system you are going to use to connect to the server.

Once both are installed you can open the client program and enter the IP address of the server to connect to it.

good luck.

---

### Post by sunstriker on 2008-05-14
Ubuntu has a built-in vnc server. it's under System -> Preferences -> Remote desktop...
the viewer is under Applications -> Internet -> Remote Desktop Viewer.
So you don't have to install Real VNC, if course you can if you insist...

---

### Post by forthepeople on 2008-05-14
you've got to remember the server is the computer you are remote controlling TO and the client is the computer you are remove controlling from. 

i believe the following starts the server/daemon
/etc/init.d/vncd

and then on the client computer (unbuntu) you can open Applications -> Internet -> Remote Desktop Viewer and select VNC as the protocol to control the computer.

---

### Post by rcor on 2008-05-14
> **KingWilliam said:**
> What are yo trying to do? Access a remote machine? Or access the system you are working on from an other location? 

VNC works with a client server. You should install the server on the machine you want to access and the client on the system you are going to use to connect to the server.

Once both are installed you can open the client program and enter the IP address of the server to connect to it.

good luck.

I'm tryin to take over an Ubuntu Linux computer with an another computer.

---

### Post by rcor on 2008-05-14
> **sunstriker said:**
> Ubuntu has a built-in vnc server. it's under System -> Preferences -> Remote desktop...
the viewer is under Applications -> Internet -> Remote Desktop Viewer.
So you don't have to install Real VNC, if course you can if you insist...

Thanks for your reply, i've found him, even the vnc server part of it. The program works just fine, but there is one other problem now: I cannot take over my Ubuntu computer when it is logged out.... How can I configure VNC so I can take over an Ubuntu computer without loggin in?

Thanks for all help!

---

### Post by KingWilliam on 2008-05-15
> **rcor said:**
> Thanks for your reply, i've found him, even the vnc server part of it. The program works just fine, but there is one other problem now: I cannot take over my Ubuntu computer when it is logged out.... How can I configure VNC so I can take over an Ubuntu computer without loggin in?

Thanks for all help!

Sorry, but you can't. To use VNC have to be logged in on the server side. If you want to connect without logging in you will need to use another method. I once used a program called XMing to do that.

XMing is a tool you can use on the client machine to connect to the XSession on the server machine. I'm not shure but i think you can enable those connections on the server machine under system>administration>log in window.

If you need more help with this let me know. I'll make some screenshots then.

---

### Post by rcor on 2008-05-28
I've found an solution:
NoMachine NX

This very good program can be found on:
[http://www.nomachine.com/](http://www.nomachine.com/)

After installing this program you can login on your ubuntu server / desktop remotely, even over the internet. Without to have logged in.

Thanks to all people that tryed to help me with this problem.

---

