---
title: "Internet Connection"
date: 2005-11-29
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-11-29
For some reason my internet connection sometimes terminates out of the blue.

amule stays connected, but firefox can't reach the server, and stays "connecting to ..." for a while, and then gives me some error message.

I have to deactivate the eth0 and activate it again, before firefox will connect.

Any suggestions?

Gabriel

---

### Post by runlevel0 on 2005-11-29
[QUOTE=GabrielWolff]For some reason my internet connection sometimes terminates out of the blue.
amule stays connected, but firefox can't reach the server, and stays "connecting to ..." for a while, and then gives me some error message.
I have to deactivate the eth0 and activate it again, before firefox will connect.
[/QUOTE]

This seems a DNS failure, perhaps it's something related to your ISP or your configuration is wrong. 

Another source of conflict could be a firewall blocking the requests from the DNS server.

The solution for the first problem is easy if you know the IPs of your ISPs DNS servers. If you don't and you won't have to wait, just use [color=#CC0000]whois[/color], it will list the DNS servers you need.

Linux can use onto 4 DNS servers, so I would advice using 2 IPs from your ISP and one more from a DNS server near you (use whois again), so that in case one DNS server causes trouble you will still have 2 more and one of them in another network. So you will have less trouble resolving IPs.

You can then use [color=#CC33CC]System > Administration > Network[/color] to set your DNS entries or edit [color=#33CC00]/etc/resolv.conf[/color] and manually add the entries.

Restart your network and wait for results.

My second guess would be the firewall. 
[color=#CC0000]**Security Risk follows**[/color]

The code below can be used to disable your firewall:

```

sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT

```

If you feel like connecting to the wild bar naked you can try if you get errors, Linux systems are safe from virii, but not form 3v33l Hax0rz (!). Read on for the safer option:

The best soultion IMHO is to install [color=#33CC00]Firestarter[/color]: Just use synaptics to download and install it. Home site is [http://www.fs-security.com/](http://www.fs-security.com/), take a look.

Start firestarter (you need sudo) with [color=#CC33CC]ALT+F2 [sudo firestarter][/color] 
Firestarter is pretty self-explanatory. The advantage is that you can see what is hitting you, and what is being blocked. Even more: You can change the policies on the fly for IPs, ranges, hostnames and ports. Just install it and watch the logs for blocked IPs which belong to your ISP's DNS servers. 

Hope this helps ;)

[i]
NOTE: I can't stat if you are newbie or veteran, so I'm sorry if I was explainig stuff in a "lame" fashion to a vet. On the other hand, if you are new and need info about just anything I explained (from what 'whois' is or how to use it) don't hesitate asking.
[/i]

---

