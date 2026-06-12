---
title: "kppp issues with default route"
date: 2005-06-29
forum: Desktop Environments
---

### Post by jradford on 2005-06-29
After adding noauth to /etc/ppp/options kppp connects to the Internet just fine.  

First question is why isnt this the default, isnt this the majority of ISPs?

Next question is kppp doesnt seem to add the default route correctly, even though it's checked
in the account setup.

As root dialing in with kppp I get an error on the console something to the effect "no such interface"
directly after the connect but before ppp0 has been brought up.  Is kppp trying to set the default
route on a interface that's not there yet? (ie on connect but before calling pppd?).

I was able to solve the problem with 2 ways.

1. after kppp connects, go to the commandline and issue 'sudo route add default ppp0'

2. Edit /etc/ppp/ip-up and add 'route add default ppp0' at the end.

#1 is tedious, and #2 seems to work, but I'm wondering if anyone else is seeing this error or knows
why kppp gives the 'no such interface' error and doesnt correctly set the default route from the gui.

Thanks,

-Jason

---

