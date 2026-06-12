---
title: "Dlink DI-701 gateway ignores my dhcp requests"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Noremacam on 2005-12-17
I've been using ubuntu now for several months. I recently moved back from my dorm to my father's house, where his internet is shared via a D-link DI-701 gateway.

The problem is, is that the dhcp server on the gateway refuses to give an ip address to anything but windows clients. Well, actually, there's one exception: it will give an ip to suse linux(why that is, I don't know).

I've tried setting up a manual ip address, and setting the gateway and the dns to go through the router(which is set to 10.1.1.50). The computer can resolve dns addresses, but it can't do anything else.

the dhclient program gives me this output(copied to paper, and back again, so may not be exact):

DHCPOFFER from 10.1.1.50
DHCPNAK from 10.1.1.50

and it repeats this text over and over again, never retrieving an ip.

I'm rather irritated. I don't want to go back to windows. Can anyone help me? I appreciate it.

---

