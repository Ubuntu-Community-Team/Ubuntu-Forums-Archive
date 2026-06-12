---
title: "TCP/IP Troubles"
date: 2005-12-08
forum: Desktop Environments
---

### Post by nic0 on 2005-12-08
Basically, I can ping my router (192.168.2.2) but when I attempt to ping my WAN address I do not get any replies. I can also ping localhost and 127.0.0.1 successfully.

When I remotely ping my computer, I get replies perfectly. (Ping from [http://network-tools.com/](http://network-tools.com/))

I used GRC.com's ShieldsUP and my computer responds to ICMP and my FTP/HTTP server appears to be up and open.

What could cause this?

I am **not** running any firewalls and I am set to DMZ on my router.

I'd really like to have [http://WAN.IP.ADD.RESS/](http://WAN.IP.ADD.RESS/) work in Apache.

Thanks.
[email]n.vitiello@my.academy.edu[/email]

---

### Post by HighPlainsDrifter on 2005-12-08
[QUOTE=nic0]Basically, I can ping my router (192.168.2.2) but when I attempt to ping my WAN address I do not get any replies.[/QUOTE]

Are you trying to ping your WAN address from inside your LAN? Your router might be the problem.

---

### Post by nic0 on 2005-12-08
Yes, but the firewall is off and my internal IP address is set to DMZ.

---

### Post by Zaventh on 2005-12-08
That's not the proper use for a DMZ host. You're better off forwarding port 80 to your internal LAN address on the router. The DMZ cannot initiation responses back to the internal LAN. It can only forward requests.

---

### Post by shakin on 2005-12-08
[QUOTE=nic0]Yes, but the firewall is off and my internal IP address is set to DMZ.[/QUOTE]

What he means is your router will not respond to WAN pings from inside the network.

What functionality are you losing? Pinging your WAN IP doesn't sound particularly useful and is probably not something people normally do (or at least I don't), but if you tell us what you're trying to accomplish maybe we can help.

---

### Post by nic0 on 2005-12-08
When I enter [http://wan.ip.addy/](http://wan.ip.addy/) locally, I want to see my webserver.

---

### Post by Zaventh on 2005-12-08
Disable DMZ. Set your router to forward port 80 to your webserver. It's that easy.

---

### Post by nic0 on 2005-12-08
[B]nic0@nic0:~$ ping -c1 my.wan.ip.addy
PING my.wan.ip.addy (my.wan.ip.addy) 56(84) bytes of data.

--- my.wan.ip.addy ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

nic0@nic0:~$[/B]


Why?

---

### Post by TrinitronX on 2005-12-08
Do you have more than 1 network card in the pc?  I've noticed with my setup that if I don't disable my ethernet nic, then it must wait for a timeout before trying my wireless card (I'm currently not using my ethernet jack).  Whenever I tried to connect to some website with both cards being active, I would get no results.  After going into  my network settings and disabling the ethernet card, it works fine.

Also, one other thing to try is manually entering dns servers into the network settings.  For some reason my router was not sending the dns server IP's over to my wireless nic.

---

