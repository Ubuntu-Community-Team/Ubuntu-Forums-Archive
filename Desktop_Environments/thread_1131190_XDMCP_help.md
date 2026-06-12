---
title: "XDMCP help"
date: 2009-04-20
forum: Desktop Environments
---

### Post by xynamax on 2009-04-20
I can't get XDMCP to work. I have the host running 32-bit Ubuntu 8.10, with a wired connection to the network getting its IP from DHCP. I have the Client running the same (32-bit Ubuntu 8.10), also with a wired connection getting its IP via DHCP. All software updates are current on both systems.

To configure the Host I went to Administration->Login Window. On the 'Remote' tab I set 'Style' to 'Same as Local'. I clicked the 'Configure XDMCP...' button and just left all the default values as they were. (Listening on UDP 177). Clicked 'Ok' out of everything. Then created a new user to login remotely as 'foo' and restarted the system.

On the Client Side I just clicked 'Options' at the GDM Login Screen, and selected "Login via XDMCP...". The host will show up as a Computer screen displaying the Gnome logo with the IP address and 'Linux 2.6.27-11-generic'. When I click on it and click 'Connect' I get a blank black screen with an 'X' for the mouse cursor. Nothing else happens on the client unless I give it a ctrl+alt+Backspace.


I've also tried Installing Firestarter and setting an Incoming connection rule to allow Port 177, but that didn't help anything.

Help please


Here's the output from netstat -an

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6000            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::6000                 :::*                    LISTEN     
udp        0      0 192.168.2.77:46891      167.206.112.138:53      ESTABLISHED
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:47359           0.0.0.0:*                          
udp6    1848      0 :::177                  :::*


```

---

### Post by i.r.id10t on 2009-06-23
Looks like it is only listening on IPv6 stuff...

---

### Post by montemj on 2009-06-30
It seems that because ipv6 is enabled, XDMCP assumes that it should only listen on udp6. 

In early versions of Ubuntu you could blacklist ipv6 and that would solve the problem (see bug [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/58071/comments/3](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/58071/comments/3)), however since we are talking about Jaunty there is no easy way to disable ipv6 because it is built into the kernel.

So until they decide to fix this little bug I think we are up the proverbial creek without a paddle.

I've tested this with both KDM and GDM, both give the same results.

---

### Post by barlowrm on 2009-07-07
same problem here.
jaunty/kde4.3rc1

---

### Post by montemj on 2009-07-07
I found a better solution for remote desktop, being as how XDMCP isn't very secure anyway.

[http://www.nomachine.com/](http://www.nomachine.com/)

Runs great on my machine, I have this plus hamachi running and it couldn't be easier. 

If you would rather have a GPL licensed solution try [http://freenx.berlios.de/](http://freenx.berlios.de/)

---

