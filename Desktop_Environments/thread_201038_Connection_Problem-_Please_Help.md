---
title: "Connection Problem- Please Help"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Hyakutaro on 2006-06-21
Hello I'm relatively very new to Ubuntu and so far I've been really enjoying. Through my experience with the distro I only encountered one major problem; I can't seem to get my connection working.

Now I used to type **sudo pppoeconf** in Ubuntu 5.10, configure everything, and the connection worked fine. However about a month ago I increased my connection speed by changing the phone nubmer for my Ethernet Card. (In Windows, if you right click the dial-up connection you see: Connect Using: ISDN channel -3Com EtherLink ... Phone Number: xxxxx).
I also connect via a proxy, but that's not a problem because I only have to configure that in Firefox, download managers etc.

I tried to type **sudo pppoeconf** in Ubuntu 6.0.6, and followed the same old process by entering username etc... However the connection does not work, I typed plog in Terminal and I got this:

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

Now when I try to setup my connection in Ubuntu, it detects all my Ethernet Adapaters etc... just like everything worked fine, I can't seem to figure out what the problem is (I mainly believe it's because of the new phone number etc)
Could someone please tell me how to get my connection working? 
Seriously, it's the only thing that's keeping me from using Ubuntu full time.

---

### Post by fouadk on 2006-08-29
man i have the same problem and coz of it im stuck in xp...please can u let me know if u have found a solution...
thnks in advance

---

### Post by lkh on 2006-08-29
Do you use ISDN or DSL for internet connection? With DSL you do not need a phone number ...

---

### Post by fouadk on 2006-08-30
man , my connection needs a pppoe dialer (i guess its a broadband connection)...it works fine in xp... did u find any solution ????
thanks in advance

---

