---
title: "Port forwarding Minecraft"
date: 2012-01-22
forum: Gaming &amp; Leisure
---

### Post by AnimatedJuzz on 2012-01-22
I'm not sure if this is in the right category, but I'm trying to port forward port 25565. 

I tried:

iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 25565 -j ACCEPT

...and [http://www.canyouseeme.org/](http://www.canyouseeme.org/) replied with:

Error: I could not see your service on 99.58.107.157 on port (25565)
Reason: Connection refused

So, am I doing it right? I'm new to iptables and all, so any help is appreciated.

---

### Post by elliotbeken on 2012-01-22
Is there a router between your minecraft server and the internet.

If there is have you opened the port on the router to point to your minecraft server >?

---

### Post by AnimatedJuzz on 2012-01-22
> Is there a router between your minecraft server and the internet.

If there is have you opened the port on the router to point to your minecraft server >?

Sorry, I forgot to mention that there is a router, and I already opened up the ports. TCP and UDP for 25565

---

### Post by elliotbeken on 2012-01-23
Do you have a firewall of the minecraft server?

I have many services running on my linux servers and i have never had to use an IPTABLE to open/forward a service. 

Have to checked you have opened the correct port to the correct IP on the router?

---

### Post by AnimatedJuzz on 2012-01-23
> Have to checked you have opened the correct port to the correct IP on the router?

[IMG]http://s17.postimage.org/jnw4m9i1p/Screenshot_2.png[/IMG]
Is that right...? These are the ports I opened through my router.

> Do you have a firewall of the minecraft server?

Yes, but opening 25565 using ufw, or just disabling the firewall does not help.

sudo ufw disable

There was some freeware tool that allowed this to work on Windows (on this same computer), so I doubt the problem anything router related.

---

### Post by a2j on 2012-01-25
this is not a minecraft issue. but rather port forwarding issue, and I'd start with router.
Can you connect to the server locally?

---

### Post by AnimatedJuzz on 2012-01-26
> Can you connect to the server locally?

Yes, it works locally.

---

### Post by AnimatedJuzz on 2012-02-01
Don't want to sound pushy, but I've been stuck in this hole for a while and it would be great if someone could help me. For some reason [this]("http://download.cnet.com/SPI-Port-Forward/3000-2651_4-10764348.html") did the job on Windows (if only they could release their source...:().
THAT really confuses me, and it makes me think it's an OS issue. Strangely enough, on Ubuntu the server works *locally*. So, any help would be appreciated.

---

### Post by AnimatedJuzz on 2012-02-03
I happened to find [http://portfwd.sourceforge.net/]("http://portfwd.sourceforge.net/"). Can I use this to forward 25565, if so, can someone help me?

---

### Post by AnimatedJuzz on 2012-02-16
Never mind, I used a port forwarding program to fix it. It was called active port forwarder. Thanks for the help! ;)

---

