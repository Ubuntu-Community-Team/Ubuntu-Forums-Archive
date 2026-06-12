---
title: "ubuntu looks good,but worth shit without internet"
date: 2006-09-02
forum: Desktop Environments
---

### Post by fouadk on 2006-09-02
i have this problem since version 5.10 and this problem remains until now with version 6.06...
the problem is simple...i cant get online...and no one have been able to help me...i have googled and searched all over the forum...no solution...
the thing is that i use a pppoe connection that works fine in xp(in xp i just create a dialer and put the phone number to be GAMBLER/SpiderS and things go just fine) but in ubuntu i cant get to the part where i supply the phone number...i used sudo pppoeconf and supplied the username and password but how to set the phone number...
```

Jun 21 13:07:01 HKRX pppd[9527]: Connect: ppp0 <--> eth1
Jun 21 13:07:06 HKRX pppd[9527]: CHAP authentication failed: M-!O^I^HM-xM-yM-^?M-?^M-^[^L@hM-H^W@hM-H^W@^PM-zM-^?M-?^PM-zM-^?M-?M-^A^IM-^@^E^V
Jun 21 13:07:06 HKRX pppd[9527]: CHAP authentication failed
Jun 21 13:07:06 HKRX pppd[9527]: Connection terminated.
Jun 21 13:07:11 HKRX pppd[9542]: PPP session is 24
Jun 21 13:07:11 HKRX pppd[9542]: Using interface ppp0
Jun 21 13:07:11 HKRX pppd[9542]: Connect: ppp0 <--> eth1
Jun 21 13:07:11 HKRX pppd[9542]: Remote message: Dialed NAS not allowed.^J
Jun 21 13:07:11 HKRX pppd[9542]: PAP authentication failed
Jun 21 13:07:11 HKRX pppd[9542]: Connection terminated.

```
this is what i get after i start the connection and type plog...
please help...im almost sure that i need to configure the phone number to be GAMBLER/SpiderS coz in xp if i dont supply this phone number it tells me that the username and/or password ar wrong...so i assume that PAP authentication failed have the same meaning of the xp error described above...please help coz i really like ubuntu but it realy worth nothing without internet...
thanks in advance

---

### Post by encompass on 2006-09-02
try looking at the man pages... or talking to the maker of the the program them selves.  The website should be in the man pages.
> man <command>

---

