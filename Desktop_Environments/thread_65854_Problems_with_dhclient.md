---
title: "Problems with dhclient"
date: 2005-09-15
forum: Desktop Environments
---

### Post by NoHope on 2005-09-15
Hello all!

I [# dhclient] when it seems works well, but after a few seconds, the internet doesn't work no more! I configured the computers to be IP automatic (win98) and my Linux station to be DHCLIENT on netword-admin, is it correct?

My PC is conected to a router 10.1.1.1

See the output of dhclient:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth2/00:07:95:b4:67:0a
Sending on   LPF/eth2/00:07:95:b4:67:0a
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:e0:7d:ca:48:49
Sending on   LPF/eth1/00:e0:7d:ca:48:49
Listening on LPF/eth0/00:08:54:21:e5:59
Sending on   LPF/eth0/00:08:54:21:e5:59
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 4
DHCPACK from 10.1.1.1
bound to 10.1.1.3 -- renewal in 137548 seconds.

then I need to [killall dhclient; dhclient] to take the web for a few seconds again...

What's the problem?

Thx! Bye!

---

