---
title: "There's no place like 127.0.0.1"
date: 2009-05-19
forum: General Help
---

### Post by Patrick Snyder on 2009-05-19
I have .html files in my /var/www


When I had ubuntu 8.10 I could go to [http://127.0.0.1/](http://127.0.0.1/) (or I or my friends could go to my normal IP address) and see the website I put there.

I upgraded to ubuntu 9.04

Now [http://127.0.0.1/](http://127.0.0.1/) and my IP address don't work any more =/



We just get:
Failed to Connect
Firefox can't establish a connection to the server at 127.0.0.1.


Can anyone help?

Thanks in advance (^_^)/
-Patrick

---

### Post by cariboo on 2009-05-19
The first question is, is the the http server running?
Question 2 is, can you connect using localhost?

---

### Post by Patrick Snyder on 2009-05-22
Hi thanks for your reply.


Forgive my ignorance, but I don't know how to check if the http server is running.  When I had 8.10, I was interested in setting up an FTP server.  So I tried vsftpd but ultimately didn't get far.  During trying, I simply went to [http://127.0.0.1/](http://127.0.0.1/) at one point and was surprised to find a generic webpage there.

I searched and found that webpage in my /var/www
I edited it and put my own things in there.


I'm not exactly sure what you mean "can you connect using localhost?"  Can you please be a bit more specific.



**_More info_**
I just tried connecting to [http://192.168.0.1/](http://192.168.0.1/)
I used to be able to connect to my router this way.  It no longer connects.  I turned my router off and back on.  Still no luck.

I just tried sudo vsftpd and got:
500 OOPS: could not bind listening IPv4 socket




Thanks for your help so far (^_^)/
Please let me know if there's anything else I can do.

---

### Post by ibuclaw on 2009-05-22
> **Patrick Snyder said:**
> Hi thanks for your reply.


Forgive my ignorance, but I don't know how to check if the http server is running.  When I had 8.10, I was interested in setting up an FTP server.  So I tried vsftpd but ultimately didn't get far.  During trying, I simply went to [http://127.0.0.1/](http://127.0.0.1/) at one point and was surprised to find a generic webpage there.

I searched and found that webpage in my /var/www
I edited it and put my own things in there.


I'm not exactly sure what you mean "can you connect using localhost?"  Can you please be a bit more specific.



**_More info_**
I just tried connecting to [http://192.168.0.1/](http://192.168.0.1/)
I used to be able to connect to my router this way.  It no longer connects.  I turned my router off and back on.  Still no luck.

I just tried sudo vsftpd and got:
500 OOPS: could not bind listening IPv4 socket




Thanks for your help so far (^_^)/
Please let me know if there's anything else I can do.

[http://localhost]("http://localhost")

And to check if webserver is running:
```
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apaches2 start

```

Regards
Iain

---

### Post by Patrick Snyder on 2009-05-23
Thank you Iain!

It told me apache2 wasn't installed so I installed it.

_These now work_
[http://localhost/](http://localhost/)
[http://127.0.0.1/](http://127.0.0.1/)
and my IP address


Interestingly, where one question got solved another arose.  I still can't get to my router while in ubuntu.

I booted into WinXP (same computer) and got into my router by going into:
[http://192.168.1.1/](http://192.168.1.1/)
But no luck in ubuntu.

This is not really a problem for me, more of a curiosity as to 'why'.  So if anyone happens to suspect why off-hand, I'd like to know. (^_^)


Thanks for your help (^_^)/
Best Wishes,
-Patrick

---

### Post by ActiveFrost on 2009-05-23
Just curious, have you tried to open these links/addresses from different browsers ( instead of trying to do the same task only via, let's say, Firefox ) ?

---

### Post by wanchai on 2009-05-23
Try "sudo ifconfig" This should show you all your networks and IP addresses. You will certainly find a network called "lo" with IP 127.0.0.1. You might also find a network "eth0", that's normally a wired network, with some IP address. If you want to connect to that router on 192.168.1.1 you need to have a network with an IP address in the same range, or in the same subnet as it's called more technically, i.e. an IP address that looks like 192.168.1.n.  If you know how to change your IP address, set it to 192.168.1.10 or so and you should be able to connect to your router again.

By the way, in Windows you can type "ipconfig /all" in a DOS box and you get similar information to what "ifconfig" will give you in Unix.

---

### Post by Patrick Snyder on 2009-05-23
> **wanchai said:**
> Try "sudo ifconfig" This should show you all your networks and IP addresses. You will certainly find a network called "lo" with IP 127.0.0.1. You might also find a network "eth0", that's normally a wired network, with some IP address. If you want to connect to that router on 192.168.1.1 you need to have a network with an IP address in the same range, or in the same subnet as it's called more technically, i.e. an IP address that looks like 192.168.1.n.  If you know how to change your IP address, set it to 192.168.1.10 or so and you should be able to connect to your router again.

By the way, in Windows you can type "ipconfig /all" in a DOS box and you get similar information to what "ifconfig" will give you in Unix.
```

patrick@patrick-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:e1:b2:94  
          inet6 addr: fe80::212:3fff:fee1:b294/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31382557 (31.3 MB)  TX bytes:3784371 (3.7 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:3a:ef:53  
          inet6 addr: fe80::212:f0ff:fe3a:ef53/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xa000 Memory:dcffd000-dcffdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31061420 (31.0 MB)  TX bytes:31061420 (31.0 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:87.15.85.152  P-t-P:217.141.105.23  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:32388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:30223917 (30.2 MB)  TX bytes:3037825 (3.0 MB)

```

My inet addr under ppp0 changes everytime I restart my computer.
I plug into the router with a cable.
I don't know how to change my IP address manually.


_**Browsers I've used to check:**_
_WinXP_
Firefox
Seamonkey

_Ubuntu_
Firefox
Konqueror
Lynx

---

### Post by thomasyen on 2009-05-23
> **Patrick Snyder said:**
> 

My inet addr under ppp0 changes everytime I restart my computer.

Maybe your IP address is assigned to your computer dynamically?

---

### Post by bruno9779 on 2009-05-23
I don't see any ipv4 addresses in your Ifconfig.
Are you using ipv6 for your LAN?

PS: the default value for gateway is 192.168.48.1, not 192.168.1.1

---

### Post by Patrick Snyder on 2009-05-23
> **thomasyen said:**
> Maybe your IP address is assigned to your computer dynamically?
It is.
I don't see how that affects my computer talking to the router though.  I could always connect by 192.168.0.1 in Intrepid.


> **bruno9779 said:**
> I don't see any ipv4 addresses in your Ifconfig.
Are you using ipv6 for your LAN?

PS: the default value for gateway is 192.168.48.1, not 192.168.1.1

[http://192.168.48.1/](http://192.168.48.1/) doesn't work for me.
In WinXP [http://192.168.1.1/](http://192.168.1.1/) worked perfectly today.  Just not in ubuntu.



I was wondering about the lack of ipv4 addresses.
I haven't configured this at all.  I'm using exactly what 9.04 gave me.  I've only set up a simple DSL connection, which is what I also had in 8.10 when it worked.


Also:
```
patrick@patrick-laptop:~$ sudo vsftpd
[sudo] password for patrick:
500 OOPS: could not bind listening IPv4 socket
```

Is it possible that my router will only talk to my browser through IPv4?
How do I give my computer an IPv4 address?
Do I even want to give it one?

---

### Post by bruno9779 on 2009-05-23
ipv4 is 192.168.1.1 kind of address.

ipv6 looks like a mac-address 00:4f:3e: ...

I asked because i haven't seen ipv6 used practically by anyone yet.

By googling your error message, i have found this post:

[http://ubuntuforums.org/showthread.php?t=264003](http://ubuntuforums.org/showthread.php?t=264003)

I hope it helps

---

### Post by wanchai on 2009-05-24
Patrick, I'd like to figure out your router problem first.

Can you please give us some details about how your network is wired up? What is connected where? Do you have more than one computer connected to the Internet? What is the model of the "router" that you are using?

Can you please do the "ipconfig /all" in Windows and confirm that the Internet is working when you do that?

There are two major kinds of devices that you can use to connect to the DSL line given to you by Telecom Italia. The first type is a simple DSL modem. This has one RJ-11 connector to connect a phone line (maybe a second to connect a telephone) and one RJ-45 to connect via Ethernet to a PC. With such a device your PC must be running pppoe to connect to the Internet, and there is nothing to configure on the modem itself. The user id and password from the ISP need to be configured on the computer, usually during installation of the network or later using some kind of script or network manager GUI.

The second type are DSL gateways or routers. These have more than one Ethernet connector and you can connect multiple computers. Some also have wireless LAN built in. In this case, the device is running pppoe and you have to configure it using a web interface as you mentioned.

It seems that currently you have a mix. You are talking about a router and that you previously connected to via [http://192.168.0.1](http://192.168.0.1) or something, but your ifconfig output shows that your computer is running ppp. To me that doesn't quite fit together. And yes, if you are running ppp, a new IP address will be assigned by the ISP every time you restart ppp.

---

