---
title: "[SOLVED] Letting Pogo.com through Firestarter (without ports)"
date: 2008-12-05
forum: General Help
---

### Post by solwic on 2008-12-05
I'm running Firestarter in restrictive (white list) mode, but I'm having a problem.  I've managed to add ports for the common stuff (http, https, pop3, pop3s, etc.), but the firewall is blocking java apps from pogo.com.  

I went to pogo's help site, and they said they don't give out ports because they change so often.  What they suggested was letting the IP through, and gave two IP addy's (159.153.235.1 and 159.153.235.2).

My question is:  how do I let these two IP's through Firestarter so my wife can play her Pogo without me having to throw the firewall into permissive mode?  I tried adding them under the policy tab, for both inbound and outbound requests...but no go.  If I put it in permissive mode, everything works fine.  

Any ideas?  I know almost nothing about firewalls, so I'm sure this is easy and I'm just being a newbie here.

Thanks!

---

### Post by solwic on 2008-12-06
Anybody?  Any ideas?

---

### Post by deadowl on 2008-12-06
Firestarter can be a real pain. One thing you can try to do is download a blacklist and find what you're looking for in the games section.

Yahoo is another site that's got issues.

---

### Post by solwic on 2008-12-06
I actually figured this out, and it had nothing to do with the software.  Pogo gave me the IP 159.153.235.1, but what was trying to connect (in the events list in Firestarter) was 159.153.23**_6**_.1

Stupid Pogo.  

Anyway, sorry for wasting the forum space.

---

