---
title: "ip masquerade"
date: 2008-12-05
forum: General Help
---

### Post by eppo on 2008-12-05
i had the hard drive in my server die. i was running hardy server on it. i decided to reinstall using 8.10. the problem i'm having is with ip masquerade. i did:
echo "1" ip_forward
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE (where eth0 is my outbound interface)
from my home network boxes, i can do a ping [www.google.com](www.google.com), and it pings fine, but if i try to go to [www.google.com](www.google.com) from a web browser it doesnt work. it just says "waiting for www.google.com" 
so i'm guessing that when the packets are coming back, the server isnt handling them correctly and not sending them back to the original machine.
anyone else have trouble with this? or can someone help me out, is there something different with 8.10 that i missed?
thanks

---

### Post by eppo on 2008-12-07
ok, so after doing a bit of research i found that, what i did was correct in hardy, but in 8.10, its different, and i found a doc on the ubuntu site, here:
[https://help.ubuntu.com/8.10/serverguide/C/firewall.html](https://help.ubuntu.com/8.10/serverguide/C/firewall.html)
i did as it said in the doc, using only iptables, still i get the same results. its working fine under 8.04.1 so unless someone has done something other than what is in that doc to get ip masquerade working, i guess i'm stuck using 8.04.1.

---

### Post by vvalero on 2009-01-15
Hi!

I have exactly the same problem in a fresh install of 8.10 server
I can do ping, traceroute, nslookup, telnet to a 110 port, etc, but can't browse web, can't download ftp files, etc.

It seems something like when you connect to a ftp server and it requires passive mode, you can list files etc, but you are unable to establish data connection.

The most extrange I see, is that I have not found anyone having this trouble except you.

Please tell me if you found a solution, I'm going crazy!!

---

### Post by eppo on 2009-01-17
nope, i just stuck with 8.04.
if you are able to find a solution let me know. i would definitely like to upgrade to 8.10.

---

### Post by jallot on 2009-01-20
> **vvalero said:**
> Hi!

I have exactly the same problem in a fresh install of 8.10 server
I can do ping, traceroute, nslookup, telnet to a 110 port, etc, but can't browse web, can't download ftp files, etc.

It seems something like when you connect to a ftp server and it requires passive mode, you can list files etc, but you are unable to establish data connection.

The most extrange I see, is that I have not found anyone having this trouble except you.

Please tell me if you found a solution, I'm going crazy!!


I've encountered the same problem when I upgraded to 8.10 today.  My Iptables configuration worked properly in 8.04.

---

### Post by eppo on 2009-01-22
any iptables guru's out there that could help out on this? it seems like when you make a http request from an internal computer, the request is sent, but not coming back through the gateway?

---

