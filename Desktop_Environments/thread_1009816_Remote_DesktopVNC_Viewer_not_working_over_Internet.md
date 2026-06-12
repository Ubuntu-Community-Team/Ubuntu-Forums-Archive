---
title: "Remote Desktop/VNC Viewer not working over Internet"
date: 2008-12-13
forum: Desktop Environments
---

### Post by pmulgaonkar on 2008-12-13
[SOLVED] Folks: I have a Hardy box behind a wireless NAT. I can connect to the box using VNC viewer from another computer on the wireless (using local IP address 192.168.1.x). The Hardy box is on a fixed IP address. I have the router set up to forward port 5900 to that fixed IP for both TCP and UDP protocols. 

The computer is using DynDNS and ddclient to report its IP address and I can ping that IP it over the internet.

However, I cannot use VNC viewer over the internet to connect to the Hardy box. I get Connection Refused 10061. How can I test if the router is actually forwarding anything to the Hardy box? Is there a remote desktop log that I can look at to see if it shows any incoming connection attempts when I try to VNC to it over the internet? 

Any help and pointers appreciated.

--p

---

### Post by hyperdude111 on 2008-12-13
I got my vnc working by going on ubuntu

System > Preferences > Remote Desktop

Select the top two options the select a password and tick the password box. Untick the "ask you" box it just wastes time.
Go to the "advanced tab" Tell it to use port 5900 and select always use an icon.

Once this is done (i dont know why) you have to re-start.

This is what i did and it works for me.

---

### Post by pmulgaonkar on 2008-12-13
Just to clarify: I have Remote Desktop working fine, but not through the NAT. How can I check if the router is actually doing what I set it to do, namely forward Port 5900 to the unix box. Is there anything I can monitor on the box to see if it received any incoming requests? Or is there anything I can do on the router to check that it is indeed forwarding the right ports to the right device?

--p

---

### Post by pmulgaonkar on 2008-12-13
Another update: I tried [www.canyouseeme.org](www.canyouseeme.org) and it shows port 5900 open. But VNC does not connect--still gets a timeout.

---

### Post by pmulgaonkar on 2008-12-15
Can anyone help? Should I post this in some other part of the forum?
--p

---

### Post by mojorising on 2009-01-02
Hi, there. Not sure if you're still having this problem but one way to see if a given service is running on that port is do try using netcat. 

Like so:
```

nc -zv localhost 5900

```

You should see something like the below:
```

username@mybox:~$ nc -zv localhost 80
localhost [127.0.0.1] 80 (www) open

```

What the above lines demonstrate is a quick port scan on port 80. Use nc --help for more options. 

If it doesn't work, you'll probably see a "Connection refused" message.

If it does, you can try the same thing from the machine you are running VNC viewer on. If that machine doesn't have netcat (the nc thing), then you can try using telnet to connect to port 5900. 

An example on using telnet is below. Substitute the IP of the VNC server for 192.168.1.123.
```

telnet 192.168.1.123 5900

```

Hopefully, you'll see something cluing you in that it's connecting via telnet (the screen might print a message saying "connected to..." or similar). If it doesn't work, you'll likely see a connection refused message here as well. It might hang, which could be another indication traffic can't connect to that port. 

Nmap is another useful tool for checking services on ports. Lots of information on it is available on the web. insecure.org is the official source for that. 


Good luck, 
Mike

---

