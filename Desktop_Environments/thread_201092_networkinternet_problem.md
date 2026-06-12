---
title: "network/internet problem"
date: 2006-06-21
forum: Desktop Environments
---

### Post by sopo_dan on 2006-06-21
i have this strange problem: nothing connects except skype and the weather applet. firefox won't open any webpage, gaim doesn't connect to any protocol, not even "ping" returns anything.
in win everything works fine, so it's not my ISP's fault

---

### Post by s_p_a_r_k_y on 2006-06-21
Ummm, first of all, cable/dsl? are you behind a proxy? are you behind a router? do you have an IP?

---

### Post by munckfish on 2006-06-21
My usual tactic for debugging these sorts of network issues is to use Ethereal to trace my network devices, then run the thing which works then the thing which doesn't. Then stop Ethereal and scour the trace for any hints as what's wrong. 9/10 times I can spot the problem doing that.

Otherwise as s p a r k y said above, info on your connection settings may help us to spot a problem.

---

### Post by sopo_dan on 2006-06-21
i'm on cable, no proxy, no router, i get my ip/gateway/dns by dhcp

---

### Post by s_p_a_r_k_y on 2006-06-21
ok, did you by chance setup any firewall on Linux (iptables?) or such? Perhaps you aren't using a nameserver? Try pinging the nameserver in /etc/resolve.conf. Try resolving some domain names as well, on the command line type
```
 host yahoo.com
```
and let us know your findings. Also try pinging your gateway if you have one. You can find it via this command 
```
 #route
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth2
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
 
```
my gateway is 192.168.1.1, so try pinging that guy.

Next if you can resolve yahoo or some domain, try wgetting something
```
 wget www.yahoo.com 
```

Perhaps you setup firefox by accident to use a proxy or something. Wget will return the homepage of whatever domain you use and save it as a file in the directory you are in, usually index.something

Hope this helps, and report back to us

---

### Post by Thought_Criminal on 2006-06-21
[QUOTE=sopo_dan]i have this strange problem: nothing connects except skype and the weather applet. firefox won't open any webpage, gaim doesn't connect to any protocol, not even "ping" returns anything.
in win everything works fine, so it's not my ISP's fault[/QUOTE]
I have a similar problem in that firefox fails to connect to websites, my weather and RSS gdesklets applets fail to connect. But the interesting thing is I can use konqueror and apt-get commands and they work well and my gdesklet network monitor shows activity for those things.

Anyways can you try 
> sudo apt-get update
Just to see if it is a connection issue or maybe the same as problem as mine which seems to be application specific.

---

### Post by sopo_dan on 2006-06-21
hmmm... things got sorted out... by themselves

it's very strange though
it wasn't a dns problem (i wrote down ip addresses from a few sites using windows and then tried connecting to those, which still wasn't working)
it wasn't a gateway problem, since weather applet and skype could connect (as far as i know the gateway is used by every outgoing connection)
and i'm not the guy to change settings and not remember that afterwards (sorry if this sounds smug, wasn't my intention)

thanks to all of you who tried to help

PS: sudo apt-get update didn't work either, nothing except weather and skype

---

