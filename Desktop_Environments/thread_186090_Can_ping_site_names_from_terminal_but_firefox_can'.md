---
title: "Can ping site names from terminal but firefox can't resolve them"
date: 2006-06-01
forum: Desktop Environments
---

### Post by bdge on 2006-06-01
I have loaded ubuntu from a CD and it looks wonderful, however there is a bizarre problem.

I can go to a terminal window and ping (eg.) google.co.uk or apple.com, no problem.

BUT if I type "google.co.uk" or "apple.com" into firefox, it sits there for ages and then times out.

This is true for all host NAMES but if I type their IP addresses into Firefox, it displays the pages immediately.

So this sort of looks like a DNS issue, because Firefox can't resolve the host names, but sort of doesn't, because a terminal session can. It's like Firefox can't use the DNS service.

I have checked the proxy settings and Firefox is definitely NOT configured to use a proxy (as the fact it can display sites using IP addresses confirms).

The rest of the machines on my LAN -- 3 windows XP boxes and a Mac Powerbook -- all connect to the same DHCP server (the ADSL router) and have no problems of this nature.

The machine is a Sony VAIO VGN-A117S but I don't think that's relevant.

Any help gratefully received.

Thanks 
bdge

---

### Post by bjc on 2006-06-02
The only thing that occurs to me is to try a new Firefox profile... :-( What messages are displayed in the status bar while it's trying to resolve the hostnames? What's network.dns.disableIPv6 set to?

---

### Post by Hanibae on 2006-06-03
In Firefox go to
About:config
search for ipv6
Make sure "network.dns.disableipv6" is set to true.
Double click it to toggle it.

---

### Post by Fruhwirth on 2006-09-16
I was having this very same problem.  The IPv6 option correctly resolved the issue system wide.  Not only is firefox now able to resolve, but so is mozilla which could not previously browse the internet either.

Might want to tell people, though, that about:config should be typed into the address bar of firefox.  Neophytes like might take as much as 20 minutes trying to figure out where to put it.

---

### Post by derrylynne on 2006-12-29
Thank you so much for this thread. I was having the same problem and now it's solved means I can sleep tidy tonight....

---

### Post by teaker1s on 2006-12-29
manually set static ip and manually set your isp DNS addresses under system,administration, networking

---

