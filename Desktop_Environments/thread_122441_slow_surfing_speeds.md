---
title: "slow surfing speeds"
date: 2006-01-27
forum: Desktop Environments
---

### Post by stepore on 2006-01-27
hey folks -- i'm installing a few dual boot (windows/ubuntu) PCs and
they've all been going well except for this last one. for some reason i
can't surf as fast on this PC as on the others, nor if i were to use a
live cd or boot into windows (on this PC).

i've tried playing with mtu settings (1492, 1500) and turning off ipv6
in /etc/modprobe.d/aliases and in firefox. but on this PC nothing i've
tried has worked. strangely again, booting into windows and using the
ubuntu live CD everything is fine. any hints on what else i can try and
what could be the cause?

just using a router and DHCP client on all the PCs. all settings were
left as default on all 3 PCs. only this one is giving me a hard time
surfing. nothing times out, but it's slow. i get speeds of 175-250KBs
on the other PCs and using live CD with this one. but running Ubuntu
off the hard-drive i only get 50-80KBs.

i know this could be many things, but i'd love suggestions.

cheers.

---

### Post by stream303 on 2006-01-28
[QUOTE=stepore]
just using a router and DHCP client on all the PCs. all settings were
left as default on all 3 PCs. only this one is giving me a hard time
surfing. nothing times out, but it's slow. i get speeds of 175-250KBs
on the other PCs and using live CD with this one. but running Ubuntu
off the hard-drive i only get 50-80KBs.
[/QUOTE]

I'd probably take a look at your **/etc/resolv.conf**
and see if the nameserver listed is actually one that your isp uses.

If not, (typically internal router-dns is listed as a private-ip nameserver address), your dns queries may be taking a while to time out.

If you can find out what the primary and backup nameservers of your isp are, you can try putting them into the network configuration for your card under the DNS tab.

Since you are running dhcp, your /etc/resolv.conf may eventually get overwritten every time you get a new lease, (and which there is a simple fix for), but let's start here and see if your speeds improve.

---

### Post by stepore on 2006-01-29
[QUOTE=stream303]
If you can find out what the primary and backup nameservers of your isp are, you can try putting them into the network configuration for your card under the DNS tab.[/QUOTE]

sorry -- forgot to mention that i've already tried adding my ISP's DNS servers to /etc/dhcp3/dhclient.conf which show up in /etc/resolv.conf, still didn't help. infact, now every reboot i notice the 'setting up network interface' script taking longer to come up and then 'synching ntpdate to ununtu's ntpserver' times out and fails ... always.

any other suggestions?

---

### Post by stream303 on 2006-01-29
Hmm..  are you getting an address from the dhcp server, ie ifconfig or network gui?

If not, does

**sudo dhclient eth0**

bring the interface up?

Maybe a timing issue with this card...

---

### Post by stepore on 2006-01-29
[QUOTE=stream303]Hmm..  are you getting an address from the dhcp server, ie ifconfig or network gui?

Maybe a timing issue with this card...[/QUOTE]

yes, of course i get an ip address from the dhcp server. i _can_ surf, just slow as hell. i can see on the bottom status bar on firefox many messeges to the effect, "waiting for ... trying a1.yahoo.blablabla ... " then the website finaly downloads completely. i'll be staring at placeholders for images on some websites for 5-10 seconds sometimes.

i've read all similar thread in this forum and google on this issue, and most of them talk about ipv6. turning it off for some worked for others nothing. why the hell would the other 2 PCs be fine, but this one not. at least not when i boot ubuntu?

---

### Post by stream303 on 2006-01-29
Hm...  I guess I'm stumped too at this point.  Any chance of a typo in that prepend line in dhclient.conf?

---

### Post by dcstar on 2006-01-29
[QUOTE=stepore]hey folks -- i'm installing a few dual boot (windows/ubuntu) PCs and
they've all been going well except for this last one. for some reason i
can't surf as fast on this PC as on the others, nor if i were to use a
live cd or boot into windows (on this PC).
......
i know this could be many things, but i'd love suggestions.

cheers.[/QUOTE]
It can be that the physical network card settings are wrong.

Do a "sudo lshw" and have a look at the negotiated speed/flow control of your Ethernet card, it could be that it is set to a mode that doesn't work well (or the driver is wrong).

---

