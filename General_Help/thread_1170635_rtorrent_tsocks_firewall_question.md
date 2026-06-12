---
title: "rtorrent tsocks firewall question"
date: 2009-05-26
forum: General Help
---

### Post by Neural oD on 2009-05-26
Hi all

I have a network, but this is the problem. I need rtorrent to run off a machine within the lan. This machine(A) does not have direct access to the internet - but goes through my proxy server(B), which also acts as the firewall. I'm trying to get rtorrent to work on (A) but am having a rather hard time! I know that I should get this to work using tsocks and maybe ssh - but not sure exactly on the configuration. 

Is there someone out there who might have a clue??

---

### Post by whoop on 2009-05-26
> **Neural oD said:**
> Hi all

I have a network, but this is the problem. I need rtorrent to run off a machine within the lan. This machine(A) does not have direct access to the internet - but goes through my proxy server(B), which also acts as the firewall. I'm trying to get rtorrent to work on (A) but am having a rather hard time! I know that I should get this to work using tsocks and maybe ssh - but not sure exactly on the configuration. 

Is there someone out there who might have a clue??
Well your firewall is probably blocking ports... You need to enable port forwarding on the "firewall".

---

### Post by Neural oD on 2009-05-26
> **whoop said:**
> Well your firewall is probably blocking ports... You need to enable port forwarding on the "firewall".
@whoop - thanks - what I have done is set port forwarding for port 1080 to machine (A).
In fact I have tried a couple of things but to no avail! My setup at the moment is such: All traffic that hits (B) on port 1080 goes to (A). I have set rtorrent to use ports 52000-52200 and use dht_port 6881. In the tsocks config file I have set it to use port 1080. Then I start rtorrent by using: tsocks rtorrent
 
I seem to be connecting to the trackers, but not the peers. So not too sure what I should do from here?

---

### Post by Neural oD on 2009-05-27
BUMP 
Any takers??

---

### Post by Neural oD on 2009-05-27
BUMP Again!!

---

### Post by infocop411 on 2009-06-21
the last update for tsocks was in 2002, tsocks never was intended to proxy incoming data, only outgoing. rtorrent can handle HTTP proxies, SOCKS proxies have yet to be implemented, they need BIND support (not sure, but it's a quote) to have two way data, same as tsocks (which in not in active development it seems)
EDIT: Forgot the link to the rtorrent bug page where I grabbed the BIND support quote from, here it is.
[http://libtorrent.rakshasa.no/ticket/850](http://libtorrent.rakshasa.no/ticket/850)

---

### Post by hibliss on 2009-06-21
> **Neural oD said:**
> (B) on port 1080 goes to (A). I have set rtorrent to use ports 52000-52200 and use dht_port 6881. In the tsocks config file I have set it to use port 1080.

You lost me. Why the port maze?

You should never use port 6881 for bittorrent as it is banned by many trackers and blocked by many peers. Pick a higher port, much higher. edit: after reading your post again, I see that the external port is 1080. I still think you will have a tough time finding help with your current setup.

I also don't understand why you have such a large port range (5200-52200?).

Use a 9 port range, get rid of port 6881 (not that it made sense originally). 

Your setup is a bit overcomplicated and to be honest I do not understand the purpose. Why not just buy a router, or use IPcop?

bittorrent port forwarding is easy, and there is no need for the current maze of ports you have, and the especially large port range has no benefit.

---

### Post by Neural oD on 2009-07-14
just a quick update here 
- got it all working within rtorrent - there are 2 variables that one must put in http_proxy=x.x.x.x:80 or whatever & proxy_address=x.x.x.x:80 or whatever

---

