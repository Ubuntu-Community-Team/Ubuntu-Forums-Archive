---
title: "what ports does Remote Desktop use, trying to use with Windows Mobile 6.5"
date: 2009-06-24
forum: General Help
---

### Post by hellride66 on 2009-06-24
what is the port that this uses, i'm trying to connect with Windows Mobile 6.5, and not having any luck....
i'm using the external ip address when trying to access it, since i'm outside the network

---

### Post by jonobr on 2009-06-24
Hello

I believe the default remote desktop port is 
5900

For the well known IANA  port numberings [HERE ]("http://www.iana.org/assignments/port-numbers")

> 
vnc-server	5900/tcp   VNC Server
vnc-server	5900/udp   VNC Server
#			   Tristan Richardson <iana&realvnc.com> March 2006
#               5901-5909  Unassigned

 

I do believe it can also use the 5901 to 5909 numbers

You could double check on your ubuntu server by doing (assuming its using port 5900)

```
sudo tcpdump -vvv port 5900
```

Launch your RDP session.

If you see packets going, there getting to your machine
You need to figure if theres a response being sent back 

If you dont see anything, it could be using a different port number so running 

sudo tcpdump -vvv will show you all packets, but you would then need to parse the data for your VNC port number

---

### Post by geirha on 2009-06-24
You can't connect to an Ubuntu box with remote desktop protocol (RDP); that's a Windows only thing (you can connect to a Windows with RDP from an Ubuntu box though). The "Remote Desktop" in Ubuntu is a vnc server, so you need a vnc client to connect to it. [TightVNC](http://en.wikipedia.org/wiki/TightVNC) is a commonly used, free vnc client that runs on Windows.

---

### Post by jonobr on 2009-06-24
Hey,

Fair point, I was mentioning RDP, but you can see in the port number, it was VNC server I gave the port number to.....

THanks for clarifying

---

