---
title: "Where do I set the DHCP servers address?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by pabc on 2005-11-03
On bringing up my eth0 which is set to obtain its numbers via DHCP

ifup -a

results in a lot of 

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval xx

then no offers recieved

I know the DHCP server isnt on 255.255.255.255 so how do I tell ubuntu to use the network number where the dhcp server resides?

Unless of course 255.255.255.255 is broadcasting to all numbers, in which case something else is wrong.

P

---

### Post by mgor on 2005-11-03
255.255.255.255 is the broadcast adress, in other words you're client is "looking" for a DHCP server in the network. if there is a working dhcp server it will respond to the request and give you an IP adress. if you don't get any response then
1) no working dhcp server present in your network
2) something is wrong with your connection

---

