---
title: "Vncviewer Local Host.localdomain:0"
date: 2005-12-13
forum: General Help
---

### Post by dpmaxey on 2005-12-13
i've used remote desktop many times before, but this is my first time using and trying to figure out how to work this "vncviewer".  i'm not sure if it is my school's firewall that prevents me from seeing my own home computer that uses Linux also, or it's just that maybe i'm doing something wrong in trying to connect to the computer the correct way.

usually, it says something like "connection reset by peer" or "connection failed".  :mad:
which ip address do i use? i'm using my correct ip address i think, the one you see when you configure your network card in the network tools.

any help would be much appreciated,
thanx.
:confused::confused::confused:
sincerely,
~kawika~

---

### Post by soulestream on 2005-12-13
how are you connected to the internet. 

Do you have a router.


soule

---

### Post by dpmaxey on 2005-12-13
i believe so, the schools firewall is a pain in the rear...but i am 99.9% sure they do.
by the way, do you think that a proxy server could help if it's the firewall's fault? if so, what is some information about setting up a proxy server to use on this desktop?
-------------------
[quote=soulestream]how are you connected to the internet. 

Do you have a router.


soule[/quote]

---

### Post by dpmaxey on 2005-12-13
this is the code i put in and received.

```
david@Bethel-Ubuntu:~$ vncviewer 192.168.0.2
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection timed out
Unable to connect to VNC server

```

---

### Post by soulestream on 2005-12-13
192.168.0.2

that is not a routable address (cant use it on the internet), which means you have a router at home, most likely.

from you home go to whatismyip.com and that will tell you, your actual internet address. 

Then you will have to open a hole in your router and forward port 5900 (probably) to the PC you want to connect to. 


as far as the schools side, they may have the port blocked and you can probably get around it, but I doubt they have it blocked. 

soule

---

### Post by dpmaxey on 2005-12-13
ok. so i have to use the internet ip address....the one i used was my network ip? ok, thanx. but how do i forward that "hole" you are talking about? because u are being very helpful...i'd like to keep having help from you.
:p
:rolleyes:any more info would be nice!:p

[quote=soulestream]192.168.0.2

that is not a routable address (cant use it on the internet), which means you have a router at home, most likely.

from you home go to whatismyip.com and that will tell you, your actual internet address. 

Then you will have to open a hole in your router and forward port 5900 (probably) to the PC you want to connect to. 


as far as the schools side, they may have the port blocked and you can probably get around it, but I doubt they have it blocked. 

soule[/quote]

---

### Post by soulestream on 2005-12-13
you need to be at home and log into your router. (read your owners manual if you dont know how) Go to the port forwarding section. (may not be named that exactly). 

then you will say accept incoming connections from 5900 and forward them to port 5900 on 192.168.0.2.

that way when you enter (your real ip address) it will be accepted on 5900 and then forward the connection from the router to your home computer. 

just make sure the pc you want is running vncserver. make sure its IP is correct and make sure you internet IP is somewhat constant. If it changes daily, you will have to setup some kind of DNS service.

---

### Post by dpmaxey on 2005-12-13
my quest dsl modem thingy has a built in networking router.  is it the same as a regular router? anyways. thanx for the help again.  port 5900....ok...got it.:D

so where would i configure this kind of setting anyways? i am connecting to the networked dsl. so it's not like the dsl is connected directly to my computer.

[quote=soulestream]you need to be at home and log into your router. (read your owners manual if you dont know how) Go to the port forwarding section. (may not be named that exactly). 

then you will say accept incoming connections from 5900 and forward them to port 5900 on 192.168.0.2.

that way when you enter (your real ip address) it will be accepted on 5900 and then forward the connection from the router to your home computer. 

just make sure the pc you want is running vncserver. make sure its IP is correct and make sure you internet IP is somewhat constant. If it changes daily, you will have to setup some kind of DNS service.[/quote]

---

### Post by soulestream on 2005-12-13
you should(should) have a way to access your router. if your IP was assigned 192.168.0.2, i would try 192.168.0.1 in a browser first to see if you get the router setup. 

if not google the model number and see how to access it.

soule

---

### Post by imagine on 2005-12-13
What operating systems can you use at your school?

What do you want to do on your computer at home when youre in school? Ie do you need access to your whole desktop? Or just to some special applications? Or do you just want to access some files?

Be aware that enabling some kind of remote control of your computer is a potential security risk. Especially if you do not really know what you're doing and you're using an unencrypted connection like vnc over the internet. I recommend that before you make your computer accessible from all over the world you should invest some time and learn how to correctly set up a ssh server. There's a [SSH howto on the wiki](https://wiki.ubuntu.com/SSHHowto) and many more guides on the net how to secure a ssh server.

Through such an encrypted ssh connection you can then send everything, also vnc. If you're school blocks all traffic except HTTP it get's more difficult, but that's also doable.

---

